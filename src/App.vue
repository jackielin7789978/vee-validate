<script>
import BaseInput from '@/components/form/BaseInput.vue'
import BaseBtn from '@/components/form/BaseBtn.vue'
import BaseSelect from '@/components/form/BaseSelect.vue'

// Vee-Validate
import { useField, useForm } from 'vee-validate'
import { object, string, number } from 'yup'

export default {
	components: {
		BaseInput,
		BaseBtn,
		BaseSelect,
	},
	data() {
		return {
			genderOptions: [
				{
					id: 1,
					text: 'Female',
				},
				{
					id: 2,
					text: 'Male',
				},
				{
					id: 3,
					text: 'Other',
				},
			],
		}
	},
	setup() {
		const validationSchema = object({
      username: string().required('請輸入使用者名稱'),
      password: string().required('請輸入密碼').min(8),
      email: string().required('請輸入電子郵件'),
      phone: number().required('請輸入電話號碼'),
      gender: string().required('請選取一個選項'),
    })

    const { handleSubmit, errors } = useForm({validationSchema})

    const sendForm = handleSubmit(val => {
      console.log(value)
    })

    const { value:username } = useField('username')
    const { value:password } = useField('password')
    const { value:email } = useField('email')
    const { value:phone } = useField('phone')
    const { value:gender } = useField('gender')

		return {
			 sendForm, errors, username, password, email, phone, gender
		}
	},
}
</script>

<template>
	<div>
		<h1 class="title">Simple Form</h1>
		<form class="simple-form" @submit="sendForm">
			<BaseInput
        v-model="username"
        :error="errors.username"
				label="username"
				type="text"
			/>
			<BaseInput v-model="password" :error="errors.password" label="password" type="password" />
			<BaseInput
        v-model="email"
        :error="errors.email"
				label="email"
				type="email"
			/>
			<BaseInput v-model="phone" :error="errors.phone" label="phone" type="number" />
			<BaseSelect v-model="gender" :error="errors.gender" label="gender" :options="genderOptions" />
			<BaseBtn />
		</form>
	</div>
</template>

<style lang="scss" scoped>
.title {
	text-align: center;
}
.simple-form {
	width: 300px;
	margin: auto;
	display: flex;
	flex-direction: column;
	align-items: flex-start;
}
</style>
