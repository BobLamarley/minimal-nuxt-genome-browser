<template>
  <div ref="jbrowse"></div>
</template>

<script setup>
  import { JBrowseLinearGenomeView, createViewState } from '@jbrowse/react-linear-genome-view'
  import * as ReactDOM from 'react-dom'
  import React from 'react'
  import { ref, watch, onMounted, reactive } from 'vue'

  const props = defineProps(['assembly', 'defaultSession', 'configuration', 'tracks'])

  const jbrowse = ref(null)

  const state = reactive({
      assembly: props.assembly,
      defaultSession: props.defaultSession,
      configuration: props.configuration,
      tracks: props.tracks,
  })

  const renderView = () => {
      const viewState = createViewState({ tracks: state.tracks, assembly: state.assembly })
      ReactDOM.render(React.createElement(JBrowseLinearGenomeView, { viewState }), jbrowse.value)
  }

  watch(
      () => ({ assembly: props.assembly, defaultSession: props.defaultSession, configuration: props.configuration, tracks: props.tracks }),
      () => {
          state.assembly = props.assembly
          state.defaultSession = props.defaultSession
          state.configuration = props.configuration
          state.tracks = props.tracks
          renderView()
      },
      { deep: true }
  )

  onMounted(() => {
      renderView()
  })
</script> 