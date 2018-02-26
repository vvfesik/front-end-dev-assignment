<template>
  <section class="component-live-stream-feed row justify-content-center">
    <div class="video col-12 col-xl-8">
      <b-embed
        type="iframe"
        aspect="16by9"
        :src="'https://www.youtube.com/embed/' + youtubeId + '?autoplay=' + autoplay + '&modestbranding=1&showinfo=0&rel=0'"
        allowfullscreen />
    </div>
    <div class="chat col-12 col-xl-4" v-show="showChat">
      <b-embed 
        type="iframe"
        :src="'https://www.youtube.com/live_chat?v=' + youtubeId + '&output=embed&embed_domain=front-end-dev-assignment.firebaseapp.com'" />
    </div>
    <div class="col-12 text-center mt-3">
      <b-button
        variant="outline-primary"
        @click="showChat = !showChat"
        v-text="showChat ? 'Hide Chat' : 'Show Chat'" />
    </div>
  </section>
</template>

<script>
export default {
  name: 'LiveStreamFeed',
  data() {
    return {
      youtubeId: 'CYq98o5YS-8',
      autoplay: '0',
      showChat: false
    };
  }
};
</script>

<style scoped>
.chat .embed-responsive {
  height: 100%;
}
.video .embed-responsive:before {
  background: url('https://img.youtube.com/vi/CYq98o5YS-8/maxresdefault.jpg') no-repeat;
  background-size: contain;
  filter: blur(3px);
}
</style>
