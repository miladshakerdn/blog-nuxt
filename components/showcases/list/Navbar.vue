<script setup lang="ts">
import MultiSelect from '~/components/forms/MultiSelect.vue'
import { LocaleCodeList } from '~/types/locale'

const route = useRoute()
const router = useRouter()
const { t, locale } = useI18n()
const appConfig = useAppConfig()

const emit = defineEmits<{
  (e: 'search',): void
}>()

// Collapse checkbox to handle overflow error
const toggle = ref(true)
const search = ref(route.query.search)
const locales = ref<string[]>(((route.query.locales || locale.value) as string).split(',').filter((el) => !!el))
const categories = ref<string[]>(((route.query.categories || '') as string).split(',').filter((el) => !!el))
const tags = ref<string[]>(((route.query.tags || '') as string).split(',').filter((el) => !!el))

const categoryOptions = computed(() => {
  return appConfig.showcaseCategories.map(category => {
    return {
      label: t(`labels.showcaseCategories.${category}`),
      value: category,
    }
  }).sort((a, b) => a.label.localeCompare(b.label))
})

const tagOptions = computed(() => {
  return appConfig.showcaseTags.map(tag => {
    return {
      label: t(`labels.showcaseTags.${tag}`),
      value: tag,
    }
  }).sort((a, b) => a.label.localeCompare(b.label))
})

const localeOptions = LocaleCodeList.map(lang => {
  return {
    label: t(`commons.labels.languages.${lang}`),
    value: lang,
  }
})

const handleSubmit = async () => {
  await router.replace({
    query: {
      locales: locales.value.length === 0 || (locales.value.length === 1 && locales.value[0] === locale.value)
        ? undefined : locales.value.join(','),
      categories: categories.value.length === 0 ? undefined : categories.value.join(','),
      tags: tags.value.length === 0 ? undefined : tags.value.join(','),
      search: search.value || undefined,
    }
  })

  emit('search')
}

const handleReset = () => {
  search.value = ''
  locales.value = [locale.value]
  categories.value = []
  tags.value = []
}
</script>

<template>
  <div
    class="collapse collapse-arrow"
    :class="{
      'mb-4': !toggle,
      'overflow-visible': toggle
    }"
  >
    <input
      v-model="toggle"
      class="min-h-0"
      type="checkbox"
    >
    <div class="collapse-title text-xl font-medium capitalize px-0 py-2 min-h-0">
      {{ t('commons.labels.search') }}
    </div>
    <div class="collapse-content px-0 overflow-visible">
      <form
        @submit.prevent="handleSubmit"
        @reset="handleReset"
      >
        <div
          v-if="toggle"
          class="grid grid-cols-1 lg:grid-cols-4 gap-2.5 lg:gap-4"
        >
          <div class="form-control w-full">
            <label class="label">
              <span class="label-text">{{ t('labels.blogFilter.locales') }}</span>
            </label>
            <MultiSelect
              v-model="locales"
              :options="localeOptions"
            />
          </div>
          <div class="form-control w-full">
            <label class="label">
              <span class="label-text">{{ t('labels.blogFilter.categories') }}</span>
            </label>
            <MultiSelect
              v-model="categories"
              :options="categoryOptions"
              :placeholder="t('labels.blogFilter.categories')"
            />
          </div>
          <div class="form-control w-full">
            <label class="label">
              <span class="label-text">{{ t('labels.blogFilter.tags') }}</span>
            </label>
            <MultiSelect
              v-model="tags"
              :options="tagOptions"
              :placeholder="t('labels.blogFilter.tags')"
            />
          </div>
          <div class="form-control w-full">
            <label class="label">
              <span class="label-text">{{ t('commons.labels.search') }}</span>
            </label>
            <input
              v-model="search"
              class="input input-bordered input-sm w-full"
              type="text"
              :placeholder="t('commons.labels.search')"
            >
          </div>
        </div>
        <div class="mt-4 flex space-x-4">
          <button
            class="btn btn-sm btn-primary rounded-btn"
            type="submit"
          >
            {{ t('commons.btns.search') }}
          </button>
          <button
            class="btn btn-sm btn-error btn-outline rounded-btn"
            type="reset"
          >
            {{ t('commons.btns.reset') }}
          </button>
        </div>
      </form>
    </div>
  </div>
</template>
