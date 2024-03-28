<script lang="ts">
import {defineComponent} from 'vue'
import WindowHeader from "@/components/UIParts/WindowHeader.vue";
import UserNote from "@/components/UIParts/UserNote.vue";
import NumberInput from "@/components/UI/PhoneField.vue";
import CustomInput from "@/components/UI/CustomInput.vue";
import PhoneField from "@/components/UI/PhoneField.vue";
import CustomButton from "@/components/UI/CustomButton.vue";
import CustomSelect from "@/components/UI/CustomSelect.vue";

export default defineComponent({
  name: "ActivationWindow",
  components: {CustomSelect, CustomButton, PhoneField, CustomInput, NumberInput, UserNote, WindowHeader},
  data(){
    return {
      isNeedHelp: true,
      isHasPromocode: false,
      username: '',
      role: '',
      usernameError: false,
      roleError: false
    }
  },
  methods:{
    save(event){
      event.preventDefault()
      this.validateFields(this.username, this.role)
    },
    validateFields(firstField, secondField){
      this.usernameError = firstField === '';
      this.roleError = secondField === '';

      console.log(this.roleError)
      if (!this.usernameError && !this.roleError) {
        // Если нет ошибок, продолжайте с отправкой данных
        console.log('Данные формы:', this.usernameError, this.roleError);
      }
    }
  }
})

</script>

<template>
  <section class="activation-window">
    <window-header>
      Активация тестового доступа
    </window-header>

    <section class="window-content">

      <span class="window-content-info font-body">
        Для активации 14 дневного тестового доступа заполните форму ниже.
      </span>

      <section class="window-content-note">
        <user-note>
          <span class="text-strong" id="notify-attention">
            Внимание!
          </span>

          <span class="font-body" id="notify-text">
            В целях безопасности обслуживание будет осуществляться только по указанному номеру телефона
          </span>
        </user-note>
      </section>

      <section class="window-content-form">
        <form
        @submit="save($event)"
        >
          <div class="window-content-inputs">

            <phone-field
                :placeholder="'Введите номер телефона*'"
                class="input"
                :mask="'+{7} (000) 000-00-00'"
                :hasError="usernameError"
            />

            <custom-input
                :placeholder="'Как к вам обращаться?*'"
                class="input"
                :hasError="roleError"
            />

            <CustomSelect
                :placeholder="'Ваша роль в компании?*'"

            >
              <option>
                Собственник
              </option>
              <option>
                Руководитель отдела продаж
              </option>
              <option>
                Технический специалист
              </option>
              <option>
                Интегратор amoCRM
              </option>
            </CustomSelect>

          </div>

          <div class="window-content-checkboxes">
            <label class="form-check">
              <input class="form-check-input" type="checkbox" v-model="isNeedHelp">
              <span class="form-check-label" :class="{'text-strong color-green' :isNeedHelp}"> Хочу получить бесплатную помощь в настройке</span>
            </label>
            <label class="form-check">
              <input class="form-check-input" type="checkbox" v-model="isHasPromocode">
              <span class="form-check-label" :class="{'text-strong' :isHasPromocode}"> У меня есть промокод</span>
            </label>
          </div>

          <div class="window-content-button_section">
            <custom-button
            :type="'submit'"
            >
              Активировать доступ
            </custom-button>
            <div class="build_section-text">
              <span class="font-body" id="notify-text">Есть вопросы? &nbsp;</span>
              <span class="text-strong" id="notify-attention">Напишите нам!</span>
            </div>
          </div>
        </form>
      </section>
    </section>
  </section>
</template>

<style scoped lang="sass">
.red input
  border: red
.activation-window
  border: 1px solid #D1DCDE
  border-radius: 4px
  .window-content
    background-color: white
    padding: 30px 40px
    #notify-text, #notify-attention
      color: #17505B
    &-info
      font-size: 1.1rem
      line-height: 19px
      font-weight: bold
      margin-bottom: 30px
    &-note
      margin-top: 30px
    &-form
      margin-top: 20px
    &-inputs
      display: flex
      flex-direction: column
      .input
        padding: 10px 0
    &-checkboxes
      display: flex
      flex-direction: column
    &-button_section
      display: flex
      justify-content: center
      flex-direction: column
      margin-top: 30px
      .build_section-text
        margin-top: 10px
        display: flex
        justify-content: center

    .form-check
      padding: 10px 10px 10px 0

</style>
