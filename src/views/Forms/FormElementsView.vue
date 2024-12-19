<script setup lang="ts">
import BreadcrumbDefault from '@/components/Breadcrumbs/BreadcrumbDefault.vue'
import ButtonDefault from '@/components/Buttons/ButtonDefault.vue'
// import CheckboxFive from '@/components/Forms/Checkboxes/CheckboxFive.vue'
// import CheckboxFour from '@/components/Forms/Checkboxes/CheckboxFour.vue'
// import CheckboxOne from '@/components/Forms/Checkboxes/CheckboxOne.vue'
// import CheckboxThree from '@/components/Forms/Checkboxes/CheckboxThree.vue'
// import CheckboxTwo from '@/components/Forms/Checkboxes/CheckboxTwo.vue'
// import DatePickerOne from '@/components/Forms/DatePicker/DatePickerOne.vue'
// import DatePickerTwo from '@/components/Forms/DatePicker/DatePickerTwo.vue'
import DefaultCard from '@/components/Forms/DefaultCard.vue'
// import SwitchFour from '@/components/Forms/Switchers/SwitchFour.vue'
// import SwitchOne from '@/components/Forms/Switchers/SwitchOne.vue'
import SwitchThree from '@/components/Forms/Switchers/SwitchThree.vue'
// import SwitchTwo from '@/components/Forms/Switchers/SwitchTwo.vue'
import DefaultLayout from '@/layouts/DefaultLayout.vue'

import { ref } from 'vue'
import MultiSelect from '@/components/Forms/MultiSelect.vue'
import SelectGroupOne from '@/components/Forms/SelectGroup/SelectGroupOne.vue'
import { QuillEditor } from '@vueup/vue-quill'
import '@vueup/vue-quill/dist/vue-quill.snow.css';
const pageTitle = ref('Create Post')
const content = ref('')

const style={
  height: '400px',
  overflow: 'auto',
  minHight: '300px',
  maxHight: '350px',
}
const toolbarOptions = [
  ['bold', 'italic', 'underline', 'strike'],      
  ['blockquote', 'code-block'],
  ['link', 'image', 'video', 'formula'],

  [{ 'header': 1 }, { 'header': 2 }],      
  [{ 'list': 'ordered'}, { 'list': 'bullet' }, { 'list': 'check' }],
  [{ 'script': 'sub'}, { 'script': 'super' }],     
  [{ 'indent': '-1'}, { 'indent': '+1' }],      
  [{ 'direction': 'rtl' }],                      

  [{ 'size': ['small', false, 'large', 'huge'] }],
  [{ 'header': [1, 2, 3, 4, 5, 6, false] }],

  [{ 'color': [] }, { 'background': [] }],         
  [{ 'font': [] }],
  [{ 'align': [] }],

  ['clean'] 
];

</script>

<template>
  <DefaultLayout>
    <!-- Breadcrumb Start -->
    <BreadcrumbDefault :pageTitle="pageTitle" />
    <!-- Breadcrumb End -->

    <!-- ====== Form Elements Section Start -->
    <div class="grid grid-cols-1 gap-9 sm:grid-cols-2">
      <div class="flex flex-col gap-9">
        <!-- Input Fields Start -->
        <DefaultCard cardTitle="Article Information">
          <div class="flex flex-col gap-5.5 p-6.5">
            <div>
              <label class="mb-3 block text-sm font-medium text-black dark:text-white">
                Post Title
              </label>
              <input
                type="text"
                placeholder="article title"
                class="w-full rounded-lg border-[1.5px] text-black border-stroke bg-transparent py-3 px-5 font-normal outline-none transition focus:border-primary active:border-primary disabled:cursor-default disabled:bg-whiter dark:text-white dark:border-form-strokedark dark:bg-form-input dark:focus:border-primary"
              />
            </div>
            <SelectGroupOne />
            <MultiSelect />
           
          </div>
        </DefaultCard>
        <!-- Input Fields End -->

        <!-- Toggle switch input Start -->
        <DefaultCard cardTitle="Feature the post">
          <div class="flex flex-col gap-5.5 p-6.5">
            <!-- <SwitchOne />
            <SwitchTwo /> -->
            <SwitchThree />
            <!-- <SwitchFour /> -->
          </div>
        </DefaultCard>
        <!-- Toggle switch input End -->

        <!-- Time and date input Start -->
        <!-- <DefaultCard cardTitle="Time and date">
          <div class="flex flex-col gap-5.5 p-6.5">
            <DatePickerOne />

            <DatePickerTwo />
          </div>
        </DefaultCard> -->
        <!-- Time and date input End -->

        <!-- File upload input Start -->
        <DefaultCard cardTitle="Featured Image">
          <div class="flex flex-col gap-5.5 p-6.5">
            <div>
              <label class="mb-3 block text-sm font-medium text-black dark:text-white">
                Attach file
              </label>
              <input
                type="file"
                class="w-full cursor-pointer rounded-lg border-[1.5px] border-stroke bg-transparent font-medium outline-none transition file:mr-5 file:border-collapse file:cursor-pointer file:border-0 file:border-r file:border-solid file:border-stroke file:bg-whiter file:py-3 file:px-5 file:hover:bg-primary file:hover:bg-opacity-10 focus:border-primary active:border-primary disabled:cursor-default disabled:bg-whiter dark:border-form-strokedark dark:bg-form-input dark:file:border-form-strokedark dark:file:bg-white/30 dark:file:text-white dark:focus:border-primary"
              />
            </div>
          </div>
        </DefaultCard>
        <!-- File upload input End -->
      </div>

      <div class="flex flex-col gap-9">
        <!-- Textarea Fields Start -->
        <DefaultCard cardTitle="Description">
          <div class="flex flex-col gap-5.5 p-6.5">
            <div>
              <label class="mb-3 block text-sm font-medium text-black dark:text-white">
                Short description
              </label>
              <textarea
                rows="6"
                placeholder="Short description"
                class="w-full rounded-lg border-[1.5px] text-black border-stroke bg-transparent py-3 px-5 font-normal outline-none transition focus:border-primary active:border-primary disabled:cursor-default disabled:bg-whiter dark:text-white dark:border-form-strokedark dark:bg-form-input dark:focus:border-primary"
              ></textarea>

              <QuillEditor :toolbar="toolbarOptions" :placeholder="'Article description'" :style="style" v-model:content="content" class="mt-5  border" />
            </div>

            <!-- <div>
              <label class="mb-3 block text-sm font-medium text-black dark:text-white">
                Active textarea
              </label>
              <textarea
                rows="6"
                placeholder="Active textarea"
                class="w-full rounded-lg border-[1.5px] text-black border-primary bg-transparent py-3 px-5 font-normal outline-none transition focus:border-primary active:border-primary disabled:cursor-default disabled:bg-whiter dark:text-white dark:bg-form-input"
              ></textarea>
            </div> -->

            <!-- <div>
              <label class="mb-3 block text-sm font-medium text-black dark:text-white">
                Disabled textarea
              </label>
              <textarea
                rows="6"
                disabled
                placeholder="Disabled textarea"
                class="w-full rounded-lg border-[1.5px] text-black border-stroke bg-transparent py-3 px-5 font-normal outline-none transition focus:border-primary active:border-primary disabled:cursor-default disabled:bg-whiter dark:text-white dark:border-form-strokedark dark:bg-form-input dark:focus:border-primary dark:disabled:bg-black"
              ></textarea>
            </div> -->
          </div>
        </DefaultCard>
        <div class="flex gap-3 justify-end">
          <div class="flex gap-3 justify-end">
          <ButtonDefault route="/" label="Save" customClasses="bg-secondary text-gray-800" />
        <ButtonDefault route="/" label="Publish" customClasses="bg-primary text-white" />
      </div>
      </div>
        <!-- Textarea Fields End -->

        <!-- Checkbox and radio -->
        <!-- <DefaultCard cardTitle="Checkbox and radio">
          <div class="flex flex-col gap-5.5 p-6.5">
            <CheckboxOne />
            <CheckboxTwo />
            <CheckboxThree />
            <CheckboxFour />
            <CheckboxFive />
          </div>
        </DefaultCard> -->
      </div>
    </div>
    <!-- ====== Form Elements Section End -->
  </DefaultLayout>
</template>
