<template>
  <Container :slim="true">
    <div class="px-4 px-md-0 mb-3">
      <router-link :to="{ name: 'home' }" class="text-gray">
        <Icon name="back" size="22" class="v-align-middle" />
        Home
      </router-link>
    </div>
    <div>
      <div class="col-12 col-lg-8 float-left pr-0 pr-lg-5">
        <div class="px-4 px-md-0">
          <h1 v-text="'Create a space'" class="mb-4" />
        </div>
        <Block>
          <div class="mb-3">
            Use an existing ENS name to create your space on.
          </div>
          <UiButton class="text-left width-full mb-3 d-flex px-3">
            <input
              v-model="id"
              class="input flex-auto"
              placeholder="e.g. yam.eth"
            />
            <a
              class="d-block py-1 mr-n2"
              target="_blank"
              href="https://docs.snapshot.page/guides/create-a-space"
            >
              <Icon name="info" size="24" class="text-gray p-1" />
            </a>
          </UiButton>
          <UiButton
            :disabled="!id.includes('.eth') && !id.includes('.xyz')"
            @click="handleSubmit"
            class="button--submit width-full"
          >
            Next
          </UiButton>
        </Block>
      </div>
    </div>
  </Container>
</template>

<script>
export default {
  data() {
    return {
      id: ''
    };
  },
  methods: {
    handleSubmit() {
      this.$router.push({ name: 'settings', params: { key: this.id } });
    }
  }
};
</script>
