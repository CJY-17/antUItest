<template>
  <a-form :form="form" :label-col="{ span: 6 }" :wrapper-col="{ span: 13 }" @submit="handleSubmit">
      <a-input-group compact>
        <!-- <a-input style="width: 20%"   v-decorator="['test', { rules: [{ required: true, message: 'Please input your note!' }] }]" />
        <a-input style="width: 30%"  v-decorator="['testq', { rules: [{ required: true, message: 'Please input your note!' }] }]" /> -->
          <a-col>
            <a-form-item label="name"><a-input v-decorator="['name', { rules: [{ required: true, message: 'Please input your name!' }] }]" /></a-form-item>
          </a-col>
          <a-col>
            <a-form-item label="age"><a-input v-decorator="['age', { rules: [{ required: true, message: 'Please input your age!' }] }]" /></a-form-item>
          </a-col>
        
      </a-input-group>
    <a-form-item label="Note">
      <a-input
        v-decorator="['note', { rules: [{ required: true, message: 'Please input your note!' }] }]"
      />
    </a-form-item>
    <a-form-item label="Gender">
      <a-select
        v-decorator="[
          'gender',
          { rules: [{ required: true, message: 'Please select your gender!' }] },
        ]"
        placeholder="Select a option and change input text above"
        @change="handleSelectChange"
      >
        <a-select-option value="male">
          male
        </a-select-option>
        <a-select-option value="female">
          female
        </a-select-option>
      </a-select>
    </a-form-item>
    <a-form-item label="单选">
      <a-radio-group v-decorator="['radio-group']">
        <a-radio value="a">
          item 1
        </a-radio>
        <a-radio value="b">
          item 2
        </a-radio>
        <a-radio value="c">
          item 3
        </a-radio>
      </a-radio-group>
    </a-form-item>
    <a-form-item label="多选">
      <a-checkbox-group
        v-decorator="['checkbox-group', { initialValue: ['A', 'B'] }]"
        style="width: 100%;"
      >
        <a-row>
          <a-col :span="8">
            <a-checkbox value="A">
              A
            </a-checkbox>
          </a-col>
          <a-col :span="8">
            <a-checkbox disabled value="B">
              B
            </a-checkbox>
          </a-col>
          <a-col :span="8">
            <a-checkbox value="C">
              C
            </a-checkbox>
          </a-col>
          <a-col :span="8">
            <a-checkbox value="D">
              D
            </a-checkbox>
          </a-col>
          <a-col :span="8">
            <a-checkbox value="E">
              E
            </a-checkbox>
          </a-col>
        </a-row>
      </a-checkbox-group>
    </a-form-item>
    <a-form-item :wrapper-col="{ span: 12, offset: 6 }">
      <a-button type="primary" html-type="submit">
        确定
      </a-button>
    </a-form-item>
  </a-form>
</template>

<script>
export default {
  data() {
    return {
      formLayout: 'horizontal',
      form: this.$form.createForm(this, { name: 'coordinated' }),
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        console.log(values);
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
    handleSelectChange(value) {
      console.log(value);
      this.form.setFieldsValue({
        note: `Hi, ${value === 'male' ? 'man' : 'lady'}!`,
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
