<script>
import Base from '../base'
import Options from './options'

export default {
  name: 'page-robohash',
  title: 'RoboHash',
  components: { Options },
  extends: Base,
  data: () => ({
    set: 'set4',
    bgset: '',
    size: '400'
  }),
  computed: {
    src () {
      const { hash, set, bgset, size } = this
      return `https://robohash.org/${hash}?set=${set}&bgset=${bgset}&size=${size}x${size}`
    }
  }
}
</script>

<template>
  <div class="max-w-full relative">
    <ProgressBar v-if="loading" />
    <AvatarImage v-bind="{ src, email }" />
    <InputCopy class="mb-5" :value="src" />
    <Options
      :set.sync="set"
      :size.sync="size"
      :bgset.sync="bgset" />

    <GeneratorLink href="https://robohash.org" />
  </div>
</template>
