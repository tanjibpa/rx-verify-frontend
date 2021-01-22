<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <div v-if="error" class="p-5 bg-red-500 overflow-hidden sm:rounded-lg">
    <p class="font-sans font-black text-lg text-center text-gray-50">Not found</p>
  </div>
  <div v-if="id" class="bg-white shadow overflow-hidden sm:rounded-lg">
    <div class="px-4 py-5 sm:px-6">
      <h3 class="text-lg leading-6 font-medium text-gray-900">
        Product Information
      </h3>
    </div>
    <div class="border-t border-gray-200">
      <dl>
        <div
          class="bg-gray-50 px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6"
        >
          <dt class="text-sm font-medium text-gray-500">Product name</dt>
          <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
            {{ product_details.name }}
          </dd>
        </div>
        <div class="bg-white px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6">
          <dt class="text-sm font-medium text-gray-500">Manufactured at</dt>
          <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
            {{ mfg_date.toLocaleDateString("en-US") }}
          </dd>
        </div>
        <div
          class="bg-gray-50 px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6"
        >
          <dt class="text-sm font-medium text-gray-500">Expired at</dt>
          <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
            {{ expiration_date.toLocaleDateString("en-US") }}
          </dd>
        </div>
        <div class="bg-white px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6">
          <dt class="text-sm font-medium text-gray-500">Raw materials</dt>
          <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
            <ul
              class="border border-gray-200 rounded-md divide-y divide-gray-200"
            >
              <li
                v-for="raw_material in product_details.raw_materials"
                class="pl-3 pr-4 py-3 flex items-center justify-between text-sm"
              >
                <div class="w-full items-center">
                  {{ raw_material.name }}
                </div>
              </li>
            </ul>
          </dd>
        </div>
      </dl>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
      default: null,
    },
    mfg_date: {
      type: Date,
      default: null,
    },
    expiration_date: {
      type: Date,
      default: null,
    },
    product_details: {
      type: Object,
      default: null,
    },
    error: {
      type: String,
      value: null,
    },
  },
};
</script>
