<template>
	<div v-if="profileCreated" class="message">
		<p class="title">Your profile has been successfuly created!</p>
		<p class="subtitle">Now please <a href="#"> sign in </a> . </p>
	</div>
	<form v-else @submit.prevent="onSubmit">
		<input
			v-model="nickname"
			type="text"
			placeholder="Nickname"
			required
			@keydown="sendToParent"
		/>
		<input
			v-model="password"
			type="password"
			placeholder="Password"
			required
			@keydown="sendToParent"
		/>
		<input
			v-model="firstName"
			type="text"
			placeholder="First Name"
			required
			@keydown="sendToParent"
		/>
		<input
			v-model="lastName"
			type="text"
			placeholder="Last Name"
			required
			@keydown="sendToParent"
		/>
		<input
			:type="elType"
			v-model="date"
			:min="minDate"
			:max="maxDate"
			placeholder="Date of Birth"
			@focus="elType = 'date'"
			@blur="checkDate"
			required
			@change="sendToParent"
			@keydown="sendToParent"
		/>
		<select
			class="country"
			v-model="country"
			name="country"
			:style="{ color: countryStyle }"
			required
			@change="sendToParent"
		>
			<option value="" disabled selected>Country</option>
			<option value="Afganistan">Afghanistan</option>
			<option value="Albania">Albania</option>
			<option value="Algeria">Algeria</option>
			<option value="American Samoa">American Samoa</option>
			<option value="Andorra">Andorra</option>
			<option value="Angola">Angola</option>
			<option value="Anguilla">Anguilla</option>
			<option value="Antigua & Barbuda">Antigua & Barbuda</option>
			<option value="Argentina">Argentina</option>
			<option value="Armenia">Armenia</option>
			<option value="Aruba">Aruba</option>
			<option value="Australia">Australia</option>
			<option value="Austria">Austria</option>
			<option value="Azerbaijan">Azerbaijan</option>
			<option value="Bahamas">Bahamas</option>
			<option value="Bahrain">Bahrain</option>
			<option value="Bangladesh">Bangladesh</option>
			<option value="Barbados">Barbados</option>
			<option value="Belarus">Belarus</option>
			<option value="Belgium">Belgium</option>
			<option value="Belize">Belize</option>
			<option value="Benin">Benin</option>
			<option value="Bermuda">Bermuda</option>
			<option value="Bhutan">Bhutan</option>
			<option value="Bolivia">Bolivia</option>
			<option value="Bonaire">Bonaire</option>
			<option value="Bosnia & Herzegovina">Bosnia & Herzegovina</option>
			<option value="Botswana">Botswana</option>
			<option value="Brazil">Brazil</option>
			<option value="British Indian Ocean Ter">British Indian Ocean Ter</option>
			<option value="Brunei">Brunei</option>
			<option value="Bulgaria">Bulgaria</option>
			<option value="Burkina Faso">Burkina Faso</option>
			<option value="Burundi">Burundi</option>
			<option value="Cambodia">Cambodia</option>
			<option value="Cameroon">Cameroon</option>
			<option value="Canada">Canada</option>
			<option value="Canary Islands">Canary Islands</option>
			<option value="Cape Verde">Cape Verde</option>
			<option value="Cayman Islands">Cayman Islands</option>
			<option value="Central African Republic">Central African Republic</option>
			<option value="Chad">Chad</option>
			<option value="Channel Islands">Channel Islands</option>
			<option value="Chile">Chile</option>
			<option value="China">China</option>
			<option value="Christmas Island">Christmas Island</option>
			<option value="Cocos Island">Cocos Island</option>
			<option value="Colombia">Colombia</option>
			<option value="Comoros">Comoros</option>
			<option value="Congo">Congo</option>
			<option value="Cook Islands">Cook Islands</option>
			<option value="Costa Rica">Costa Rica</option>
			<option value="Cote DIvoire">Cote DIvoire</option>
			<option value="Croatia">Croatia</option>
			<option value="Cuba">Cuba</option>
			<option value="Curaco">Curacao</option>
			<option value="Cyprus">Cyprus</option>
			<option value="Czech Republic">Czech Republic</option>
			<option value="Denmark">Denmark</option>
			<option value="Djibouti">Djibouti</option>
			<option value="Dominica">Dominica</option>
			<option value="Dominican Republic">Dominican Republic</option>
			<option value="East Timor">East Timor</option>
			<option value="Ecuador">Ecuador</option>
			<option value="Egypt">Egypt</option>
			<option value="El Salvador">El Salvador</option>
			<option value="Equatorial Guinea">Equatorial Guinea</option>
			<option value="Eritrea">Eritrea</option>
			<option value="Estonia">Estonia</option>
			<option value="Ethiopia">Ethiopia</option>
			<option value="Falkland Islands">Falkland Islands</option>
			<option value="Faroe Islands">Faroe Islands</option>
			<option value="Fiji">Fiji</option>
			<option value="Finland">Finland</option>
			<option value="France">France</option>
			<option value="French Guiana">French Guiana</option>
			<option value="French Polynesia">French Polynesia</option>
			<option value="French Southern Ter">French Southern Ter</option>
			<option value="Gabon">Gabon</option>
			<option value="Gambia">Gambia</option>
			<option value="Georgia">Georgia</option>
			<option value="Germany">Germany</option>
			<option value="Ghana">Ghana</option>
			<option value="Gibraltar">Gibraltar</option>
			<option value="Great Britain">Great Britain</option>
			<option value="Greece">Greece</option>
			<option value="Greenland">Greenland</option>
			<option value="Grenada">Grenada</option>
			<option value="Guadeloupe">Guadeloupe</option>
			<option value="Guam">Guam</option>
			<option value="Guatemala">Guatemala</option>
			<option value="Guinea">Guinea</option>
			<option value="Guyana">Guyana</option>
			<option value="Haiti">Haiti</option>
			<option value="Hawaii">Hawaii</option>
			<option value="Honduras">Honduras</option>
			<option value="Hong Kong">Hong Kong</option>
			<option value="Hungary">Hungary</option>
			<option value="Iceland">Iceland</option>
			<option value="Indonesia">Indonesia</option>
			<option value="India">India</option>
			<option value="Iran">Iran</option>
			<option value="Iraq">Iraq</option>
			<option value="Ireland">Ireland</option>
			<option value="Isle of Man">Isle of Man</option>
			<option value="Israel">Israel</option>
			<option value="Italy">Italy</option>
			<option value="Jamaica">Jamaica</option>
			<option value="Japan">Japan</option>
			<option value="Jordan">Jordan</option>
			<option value="Kazakhstan">Kazakhstan</option>
			<option value="Kenya">Kenya</option>
			<option value="Kiribati">Kiribati</option>
			<option value="Korea North">Korea North</option>
			<option value="Korea Sout">Korea South</option>
			<option value="Kuwait">Kuwait</option>
			<option value="Kyrgyzstan">Kyrgyzstan</option>
			<option value="Laos">Laos</option>
			<option value="Latvia">Latvia</option>
			<option value="Lebanon">Lebanon</option>
			<option value="Lesotho">Lesotho</option>
			<option value="Liberia">Liberia</option>
			<option value="Libya">Libya</option>
			<option value="Liechtenstein">Liechtenstein</option>
			<option value="Lithuania">Lithuania</option>
			<option value="Luxembourg">Luxembourg</option>
			<option value="Macau">Macau</option>
			<option value="Macedonia">Macedonia</option>
			<option value="Madagascar">Madagascar</option>
			<option value="Malaysia">Malaysia</option>
			<option value="Malawi">Malawi</option>
			<option value="Maldives">Maldives</option>
			<option value="Mali">Mali</option>
			<option value="Malta">Malta</option>
			<option value="Marshall Islands">Marshall Islands</option>
			<option value="Martinique">Martinique</option>
			<option value="Mauritania">Mauritania</option>
			<option value="Mauritius">Mauritius</option>
			<option value="Mayotte">Mayotte</option>
			<option value="Mexico">Mexico</option>
			<option value="Midway Islands">Midway Islands</option>
			<option value="Moldova">Moldova</option>
			<option value="Monaco">Monaco</option>
			<option value="Mongolia">Mongolia</option>
			<option value="Montserrat">Montserrat</option>
			<option value="Morocco">Morocco</option>
			<option value="Mozambique">Mozambique</option>
			<option value="Myanmar">Myanmar</option>
			<option value="Nambia">Nambia</option>
			<option value="Nauru">Nauru</option>
			<option value="Nepal">Nepal</option>
			<option value="Netherland Antilles">Netherland Antilles</option>
			<option value="Netherlands">Netherlands (Holland, Europe)</option>
			<option value="Nevis">Nevis</option>
			<option value="New Caledonia">New Caledonia</option>
			<option value="New Zealand">New Zealand</option>
			<option value="Nicaragua">Nicaragua</option>
			<option value="Niger">Niger</option>
			<option value="Nigeria">Nigeria</option>
			<option value="Niue">Niue</option>
			<option value="Norfolk Island">Norfolk Island</option>
			<option value="Norway">Norway</option>
			<option value="Oman">Oman</option>
			<option value="Pakistan">Pakistan</option>
			<option value="Palau Island">Palau Island</option>
			<option value="Palestine">Palestine</option>
			<option value="Panama">Panama</option>
			<option value="Papua New Guinea">Papua New Guinea</option>
			<option value="Paraguay">Paraguay</option>
			<option value="Peru">Peru</option>
			<option value="Phillipines">Philippines</option>
			<option value="Pitcairn Island">Pitcairn Island</option>
			<option value="Poland">Poland</option>
			<option value="Portugal">Portugal</option>
			<option value="Puerto Rico">Puerto Rico</option>
			<option value="Qatar">Qatar</option>
			<option value="Republic of Montenegro">Republic of Montenegro</option>
			<option value="Republic of Serbia">Republic of Serbia</option>
			<option value="Reunion">Reunion</option>
			<option value="Romania">Romania</option>
			<option value="Russia">Russia</option>
			<option value="Rwanda">Rwanda</option>
			<option value="St Barthelemy">St Barthelemy</option>
			<option value="St Eustatius">St Eustatius</option>
			<option value="St Helena">St Helena</option>
			<option value="St Kitts-Nevis">St Kitts-Nevis</option>
			<option value="St Lucia">St Lucia</option>
			<option value="St Maarten">St Maarten</option>
			<option value="St Pierre & Miquelon">St Pierre & Miquelon</option>
			<option value="St Vincent & Grenadines">St Vincent & Grenadines</option>
			<option value="Saipan">Saipan</option>
			<option value="Samoa">Samoa</option>
			<option value="Samoa American">Samoa American</option>
			<option value="San Marino">San Marino</option>
			<option value="Sao Tome & Principe">Sao Tome & Principe</option>
			<option value="Saudi Arabia">Saudi Arabia</option>
			<option value="Senegal">Senegal</option>
			<option value="Seychelles">Seychelles</option>
			<option value="Sierra Leone">Sierra Leone</option>
			<option value="Singapore">Singapore</option>
			<option value="Slovakia">Slovakia</option>
			<option value="Slovenia">Slovenia</option>
			<option value="Solomon Islands">Solomon Islands</option>
			<option value="Somalia">Somalia</option>
			<option value="South Africa">South Africa</option>
			<option value="Spain">Spain</option>
			<option value="Sri Lanka">Sri Lanka</option>
			<option value="Sudan">Sudan</option>
			<option value="Suriname">Suriname</option>
			<option value="Swaziland">Swaziland</option>
			<option value="Sweden">Sweden</option>
			<option value="Switzerland">Switzerland</option>
			<option value="Syria">Syria</option>
			<option value="Tahiti">Tahiti</option>
			<option value="Taiwan">Taiwan</option>
			<option value="Tajikistan">Tajikistan</option>
			<option value="Tanzania">Tanzania</option>
			<option value="Thailand">Thailand</option>
			<option value="Togo">Togo</option>
			<option value="Tokelau">Tokelau</option>
			<option value="Tonga">Tonga</option>
			<option value="Trinidad & Tobago">Trinidad & Tobago</option>
			<option value="Tunisia">Tunisia</option>
			<option value="Turkey">Turkey</option>
			<option value="Turkmenistan">Turkmenistan</option>
			<option value="Turks & Caicos Is">Turks & Caicos Is</option>
			<option value="Tuvalu">Tuvalu</option>
			<option value="Uganda">Uganda</option>
			<option value="United Kingdom">United Kingdom</option>
			<option value="Ukraine">Ukraine</option>
			<option value="United Arab Erimates">United Arab Emirates</option>
			<option value="United States of America">United States of America</option>
			<option value="Uraguay">Uruguay</option>
			<option value="Uzbekistan">Uzbekistan</option>
			<option value="Vanuatu">Vanuatu</option>
			<option value="Vatican City State">Vatican City State</option>
			<option value="Venezuela">Venezuela</option>
			<option value="Vietnam">Vietnam</option>
			<option value="Virgin Islands (Brit)">Virgin Islands (Brit)</option>
			<option value="Virgin Islands (USA)">Virgin Islands (USA)</option>
			<option value="Wake Island">Wake Island</option>
			<option value="Wallis & Futana Is">Wallis & Futana Is</option>
			<option value="Yemen">Yemen</option>
			<option value="Zaire">Zaire</option>
			<option value="Zambia">Zambia</option>
			<option value="Zimbabwe">Zimbabwe</option>
		</select>
		<div class="gender">
			<label class="container">
				Male
				<input type="radio" name="gender" value="male" v-model="gender" />
				<div class="background"></div>
			</label>
			<label class="container">
				Female
				<input type="radio" name="gender" value="female" v-model="gender" />
				<div class="background"></div>
			</label>
			<label class="container">
				Intersex
				<input type="radio" name="gender" value="intersex" v-model="gender" checked />
				<div class="background"></div>
			</label>
		</div>
		<input class="submit" type="submit" value="Join us →" />
	</form>
</template>

<script>
export default {
	data() {
		return {
			elType: 'text',
			minDate: '1920-01-01',
			maxDate: '2008-08-21',

			nickname: '',
			password: '',
			firstName: '',
			lastName: '',
			date: '',
			country: '',
			gender: 'intersex',

			profileCreated: false,
		}
	},
	methods: {
		checkDate() {
			if (this.date) {
				this.elType = 'date'
				const date = new Date(this.date)
				const minDate = new Date(this.minDate)
				const maxDate = new Date(this.maxDate)
				if (date < minDate || date > maxDate) {
					this.date = ''
					this.elType = 'text'
				}
			} else {
				this.elType = 'text'
			}
		},
		sendToParent() {
			let speed = 1

			if (this.nickname) speed++
			if (this.password) speed++
			if (this.firstName) speed++
			if (this.lastName) speed++
			if (this.date) speed++
			if (this.country) speed++

			this.$emit('changed', speed)
		},
		onSubmit() {
			this.$emit('submitted', true)
			this.profileCreated = true
		},
	},
	computed: {
		countryStyle() {
			if (this.country) return 'rgba(0, 0, 0, 1)'
			return 'rgba(0, 0, 0, 0.6)'
		},
	},
}
</script>

<style>
.message {
	display: flex;
	flex-direction: column;
	width: 20rem;
	border-radius: 0.5rem;
	border: 0.2rem solid #efefef;
	padding: 1rem 2rem;
}
.message > * {
	text-align: center;
}
.title {
	margin-bottom: 2rem;
	font-weight: 300;
	font-size: 1.6rem;
}
.subtitle a {
	color: #ff50cf;
	text-decoration: none;
}
.subtitle a:hover {
	color: #d644af;
}

form {
	display: flex;
	flex-direction: column;
	width: 20rem;
	border-radius: 0.5rem;
	border: 0.2rem solid #efefef;
	padding: 1rem 2rem;
}
form > *:not(input:last-child) {
	margin-bottom: 1rem;
}

form > * {
	height: 2.5rem;
	border-radius: 0.2rem;
}

form > *:not(.gender):not(.submit):not(select) {
	padding: 0 0.5rem;
	border: 0.1rem solid rgba(0, 0, 0, 0.2);
	font-size: 1rem;
}

form > *:not(.gender):not(.submit)::placeholder {
	color: rgba(0, 0, 0, 0.6);
	font-size: 1rem;
}

select {
	padding: 0 0.3rem;
	border: 0.1rem solid rgba(0, 0, 0, 0.2);
	font-size: 1rem;
}

option:not([disabled]) {
	color: rgba(0, 0, 0, 1);
}

.gender {
	display: flex;
	justify-content: space-between;
}

.container {
	flex: 0.3;
	display: flex;
	justify-content: center;
	align-items: center;
	position: relative;
	padding: 0.5rem;
	margin-right: 1rem;
	cursor: pointer;
	font-size: 1rem;
	color: rgba(0, 0, 0, 0.6);
}

.container:last-child {
	margin: 0;
}

.container input {
	position: absolute;
	opacity: 0;
	cursor: pointer;
	height: 100%;
	width: 100%;
	z-index: 1;
	padding: 0;
	margin: 0;
}

.container:hover input ~ .background {
	background-color: rgb(245, 245, 245);
}

.background {
	position: absolute;
	width: 100%;
	height: 100%;
	border: 0.1rem solid rgba(0, 0, 0, 0.2);
	border-radius: 0.2rem;
	z-index: -1;
}

.container input:checked ~ .background {
	background-color: rgba(0, 0, 0, 0.2);
}

.submit {
	background-color: #ffff0b;
	border: 0;
	font-weight: bold;
	font-size: 1rem;
	cursor: pointer;
}

.submit:hover {
	background-color: #f0f00e;
}
</style>
