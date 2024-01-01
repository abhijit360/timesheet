<template>
    <v-card
            class="pa-4" 
            :style="{
              width: '300px'
            }"
          >
            <v-list>
              <v-list-item
                :prepend-avatar="googleProfileData.picture"
                :title="googleProfileData.name"
              >
                <template v-slot:append>
                    <v-btn
                      @click="showDialog(true, TestComponent, {}, {})"  // how do I work with this
                      flat
                      icon="mdi-cog"
                    ></v-btn>
                  </template>
              </v-list-item>
              <v-list-item>
                <v-switch
                  @change="KeepLoggedInHandler"
                  v-model="KeepLoggedIn"
                  color="purple"
                  label="Stay Logged In"
                  ></v-switch>
              </v-list-item>

            </v-list>
            <v-divider></v-divider>
            <v-card-actions>
              <v-btn
                @click="logOutHandler"
                variant="text"
                prepend-icon="mdi-logout"
              >Log Out</v-btn>
              <v-spacer></v-spacer>
              <v-btn
                variant="text"
                @click="closeMenuHandler"
              >Close</v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
</template>
<script setup lang="ts">
  import {defineEmits, ref} from "vue"
  const emit = defineEmits(['LogOut', "CloseMenu", "KeepLoggedIn"])

  const KeepLoggedIn = ref<any>() // unsure what the switch stores.

  const logOutHandler = () =>{
    emit("LogOut",false)
  }

  const closeMenuHandler = () =>{
    emit("CloseMenu", false)
  }

  const KeepLoggedInHandler = () =>{
    emit("KeepLoggedIn", KeepLoggedIn.value)
  }
</script>

