<template>
  <el-card class="form-class">
    <el-form :model="formData" :rules="rules" label-position="top" ref="mainForm">
      <el-form-item label="Type" prop="type">
        <el-select
          class="type-select"
          v-model="formData.type"
          placeholder="Choose type..."
        >
          <el-option label="Income" value="INCOME"></el-option>
          <el-option label="Outcome" value="OUTCOME"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="Comments" prop="comment">
        <el-input v-model="formData.comment"></el-input>
      </el-form-item>
      <el-form-item label="Value" prop="value">
        <el-input v-model.number="formData.value"></el-input>
      </el-form-item>
      <el-button type="primary" @click="onSubmit">Submit</el-button>
    </el-form>
  </el-card>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      formData: {
        type: "INCOME",
        comment: "",
        value: 0,
      },
      rules: {
        comment: [
          {
            required: true,
            message: "Please, write your commet below",
            trigger: "change",
          },
        ],
        value: [
          {
            required: true,
            message: "Please, type a value",
            trigger: "change",
          },
          {
            type: 'number',
            message: "Value must be a number",
            trigger: "change",
          },
        ],
      },
    };
  },

  methods: {
    onSubmit() {
        this.$refs.mainForm.validate(valid => {
            if (valid) {
                this.$emit('submitForm', {...this.formData});
                this.$refs.mainForm.resetFields()
            }
        })
    },
  },
};
</script>

<style>
.form-class {
  max-width: 500px;
  margin: auto;
}
.type-select {
  width: 100%;
}

</style>