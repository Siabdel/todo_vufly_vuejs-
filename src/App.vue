<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>Mon Application Vuetify</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container>
        <v-row>
          <v-col cols="12" md="6">
            <v-card>
              <v-card-title>Liste des tâches</v-card-title>
              <v-card-text>
                <v-list>
                  <v-list-item v-for="(task, index) in tasks" :key="index">
                    <v-list-item-content>
                      <v-list-item-title>{{ task }}</v-list-item-title>
                    </v-list-item-content>
                    <v-list-item-action>
                      <v-btn icon @click="removeTask(index)">
                        <v-icon>mdi-delete</v-icon>
                      </v-btn>
                    </v-list-item-action>
                  </v-list-item>
                </v-list>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" md="6">
            <v-card>
              <v-card-title>Ajouter une tâche</v-card-title>
              <v-card-text>
                <v-form @submit.prevent="addTask">
                  <v-text-field
                    v-model="newTask"
                    label="Nouvelle tâche"
                    required
                  ></v-text-field>
                  <v-btn type="submit" color="primary">Ajouter</v-btn>
                </v-form>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      tasks: ['Apprendre Vue.js', 'Maîtriser Vuetify', 'Créer une application'],
      newTask: ''
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push(this.newTask)
        this.newTask = ''
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>
