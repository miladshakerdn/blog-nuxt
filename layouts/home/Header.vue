<script setup lang="ts">
import { Icon } from '@iconify/vue'
import LanguageSelect from '~/components/forms/LanguageSelect'
import MenuItem from '~/layouts/home/MenuItem.vue'

const { t } = useI18n()

const isScrolled = ref(false)

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})

const handleScroll = () => {
  isScrolled.value = window.scrollY > 0
}

</script>
<template>
  <header
    class="navbar bg-base-300 z-10 fixed top-0 transition duration-500 ease-in-out"
    :class="{
      'bg-transparent': !isScrolled,
    }"
  >
    <nav class="max-w-4xl mx-auto flex w-full">
      <label
        for="home-layout-drawer"
        class="btn btn-ghost btn-sm drawer-button block lg:hidden"
      >
        <span class="text-2xl">
          <Icon
            icon="material-symbols:menu-rounded"
          />
        </span>
      </label>
      <div class="text-lg font-bold ml-2">
        {{ t('seo.title') }}
      </div>
      <div class="ml-auto" />
      <div class="space-x-4 hidden lg:flex">
        <MenuItem to="/">
          home
        </MenuItem>
        <MenuItem
          to="/blogs"
        >
          blogs
        </MenuItem>
        <MenuItem
          to="/showcases"
        >
          showcases
        </MenuItem>
        <MenuItem
          to="/contact"
        >
          contact
        </MenuItem>
      </div>
      <LanguageSelect
        class="hidden lg:block"
        end
      />
    </nav>
  </header>
</template>
