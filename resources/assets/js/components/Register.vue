<template>
    <div>
        <b-alert show>회원 가입</b-alert>
        <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group id="exampleInputGroup1"
                          label="메일 주소:"
                          label-for="exampleInput1"
                          description="We'll never share your email with anyone else.">
                <b-form-input id="exampleInput1"
                              type="email"
                              v-model="form.email"
                              required
                              placeholder="Enter email">
                </b-form-input>
            </b-form-group>
            <b-form-group id="exampleInputGroup2"
                          label="주인의 이름:"
                          label-for="exampleInput2">
                <b-form-input id="exampleInput2"
                              type="text"
                              v-model="form.name"
                              required
                              placeholder="Enter name">
                </b-form-input>
            </b-form-group>
            <b-form-group id="exampleInputGroup3"
                          label="직업:"
                          label-for="exampleInput3">
                <b-form-select id="exampleInput3"
                               :options="foods"
                               required
                               v-model="form.food">
                </b-form-select>
            </b-form-group>
            <b-form-group id="exampleGroup4">
                <b-form-checkbox-group v-model="form.checked" id="exampleChecks">
                    <b-form-checkbox value="me">체크하면 호구</b-form-checkbox>
                    <b-form-checkbox value="that">체크하면 붕딱</b-form-checkbox>
                </b-form-checkbox-group>
            </b-form-group>
            <b-button type="submit" variant="primary">등록하기</b-button>
            <b-button type="reset" variant="danger">초기화</b-button>
        </b-form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    email: '',
                    name: '',
                    food: null,
                    checked: []
                },
                foods: [
                    {text: 'Select One', value: null},
                    '요리사', '변호사', '세무사', '살모사'
                ],
                show: true
            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault();
                alert(JSON.stringify(this.form));
            },
            onReset(evt) {
                evt.preventDefault();
                /* Reset our form values */
                this.form.email = '';
                this.form.name = '';
                this.form.food = null;
                this.form.checked = [];
                /* Trick to reset/clear native browser form validation state */
                this.show = false;
                this.$nextTick(() => {
                    this.show = true
                });
            }
        }
    }
</script>

<style scoped>

</style>