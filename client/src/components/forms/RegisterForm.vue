<template>
    <form @submit.prevent="submitHandler">
        <div class="row mb-2">
            <div class="col">
                <label for="firstName">First name</label>
                <input type="text" class="form-control" :class="{ 'is-invalid': v$.firstName.$error }"
                    placeholder="i.e. Michel" aria-label="First name" id="firstName" v-model="data.firstName" />
                <div class="invalid-feedback" v-if="v$.firstName.$error">
                    <div v-for="error in v$.firstName.$errors" :key="error.$message">
                        {{ error.$message }}
                    </div>
                </div>
            </div>
            <div class="col">
                <label for="lastName">Last name</label>
                <input type="text" class="form-control" :class="{ 'is-invalid': v$.lastName.$error }"
                    placeholder="i.e. Jackson" aria-label="Last name" id="lastName" v-model="data.lastName" />
                <div class="invalid-feedback" v-if="v$.lastName.$error">
                    {{ v$.lastName.$errors[0].$message }}
                </div>
            </div>
        </div>
        <div class="row mb-2">
            <div class="col">
                <label for="email">Email address</label>
                <input type="email" class="form-control" :class="{ 'is-invalid': v$.email.$error }"
                    placeholder="i.e. michel@gmail.com" aria-label="Email address" id="email" v-model="data.email" />
                <div class="invalid-feedback" v-if="v$.email.$error">
                    <div v-for="error in v$.email.$errors" :key="error.$message">
                        {{ error.$message }}
                    </div>
                </div>
            </div>
        </div>
        <div class="row mb-2">
            <div class="col">
                <label for="password">Password</label>
                <input type="password" class="form-control" :class="{ 'is-invalid': v$.password.$error }"
                    placeholder="Enter a strong password" aria-label="password" id="password" v-model="data.password" />
                <div class="invalid-feedback" v-if="v$.password.$error">
                    <div v-for="error in v$.password.$errors" :key="error.$message">
                        {{ error.$message }}
                    </div>
                </div>
            </div>
            <div class="col">
                <label for="c-password">Confirm password</label>
                <input type="password" class="form-control" :class="{ 'is-invalid': v$.confirmPassword.$error }"
                    placeholder="Retype password" aria-label="c-password" id="c-password"
                    v-model="data.confirmPassword" />
                <div class="invalid-feedback" v-if="v$.confirmPassword.$error">
                    <div v-for="error in v$.confirmPassword.$errors" :key="error.$message">
                        {{ error.$message }}
                    </div>
                </div>
            </div>
        </div>
        <div class="row mb-2">
            <div class="col">
                <label for="nid">National ID card</label>
                <input type="text" class="form-control" :class="{ 'is-invalid': v$.nid.$error }"
                    placeholder="i.e. 5110366480" aria-label="nid" id="nid" v-model="data.nid" />
                <div class="invalid-feedback" v-if="v$.nid.$error">
                    <div v-for="error in v$.nid.$errors" :key="error.$message">
                        {{ error.$message }}
                    </div>
                </div>
            </div>
            <div class="col">
                <label for="dob">Date of birth</label>
                <input type="date" class="form-control" :class="{ 'is-invalid': v$.dob.$error }"
                    placeholder="i.e. Jackson" aria-label="dob" id="dob" v-model="data.dob" />
                <div class="invalid-feedback" v-if="v$.dob.$error">
                    <div v-for="error in v$.dob.$errors" :key="error.$message">
                        {{ error.$message }}
                    </div>
                </div>
            </div>
        </div>
        <div class="row mb-2">
            <div class="col">
                <input class="form-check-input" type="checkbox" value="" id="agreement" v-model="data.agree" />
                <label class="form-check-label ms-1" for="agreement">
                    Accept terms and conditions
                </label>
            </div>
        </div>
        <button v-if="!data.isLoading" type="submit" class="btn btn-primary mb-2" :class="{ 'disabled': !data.agree }">
            <font-awesome-icon icon="fa-solid fa-right-to-bracket" /> Register
        </button>
        <button v-else class="btn btn-primary mb-2" type="button" disabled>
            <span class="spinner-border spinner-border-sm me-1" role="status" aria-hidden="true"></span>
            Processing...
        </button>
        <div>
            <router-link class="primary-clr" :to="{ name: 'login' }">
                Already have an account? <span class="fw-bold">Login</span>
            </router-link>
        </div>
    </form>
</template>

<script>

export default {
    name: 'RegisterForm',
    props: {
        data: Object,
        v$: Object,
        submitHandler: Function,
    },
    setup(props) {
        // console.log(props.data);
    }
}
</script>

<style scoped>
a {
    font-size: 0.9rem;
}

input[type="checkbox"] {
    width: 15px;
    height: 15px;
    padding: 0;
    margin: 0;
    vertical-align: bottom;
    position: relative;
    top: -1px;
}
</style>
