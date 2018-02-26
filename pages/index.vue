<template>
  <section class="container">
    <div class="row">
      <div class="col text-center">
        <b-button-group class="mt-5 mb-5">
          <b-button
            v-for="component in components"
            :key="component.id"
            v-text="component.title"
            :variant="activeComponent === component.id ? 'primary' : 'outline-primary'"
            @click="activeComponent = component.id" />
        </b-button-group>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <transition name="slide-fade" mode="out-in">
          <keep-alive>
            <component :is="activeComponent" />
          </keep-alive>
        </transition>
      </div>
    </div>
  </section>
</template>

<script>
import LiveStreamFeed from '~/components/LiveStreamFeed';
import Form from '~/components/Form';
import Lookup from '~/components/Lookup';

export default {
  components: {
    LiveStreamFeed,
    AppForm: Form,
    Lookup
  },
  data() {
    return {
      activeComponent: 'live-stream-feed',
      components: [
        { id: 'live-stream-feed', title: 'Live Stream Feed from Youtube' },
        { id: 'app-form', title: 'Entry Form' },
        { id: 'lookup', title: 'Data Lookup' }
      ]
    }
  }
};
</script>

<style>
.slide-fade-enter-active {
  transition: all .3s ease-out;
}
.slide-fade-leave-active {
  transition: all .3s ease-out;
}
.slide-fade-enter, .slide-fade-leave-to {
  transform: translateY(10px);
  opacity: 0;
}
</style>
