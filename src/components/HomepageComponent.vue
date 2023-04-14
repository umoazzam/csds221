<template>
  <v-app-bar color="primary">
    <v-container>
      <v-row>
        <v-col cols="6" class="text-end">
          <v-icon icon="mdi-menu" /> FRAMEWORKS
        </v-col>
        <v-col cols="6">
          <v-row class="d-flex" justify="end">
            <AddEditDialogue :taskList="taskList" :addDialog="true" />
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-app-bar>
  <v-main>
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-table fixed-header>
            <thead>
              <tr>
                <th class="text-center">Title</th>
                <th class="text-center">Description</th>
                <th class="text-center">Deadline</th>
                <th class="text-center">Priority</th>
                <th class="text-center">Is Complete</th>
                <th class="text-center">Action</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="task in taskList" :key="task.title">
                <td class="text-center">{{ task.title }}</td>
                <td class="text-center">{{ task.description }}</td>
                <td class="text-center">{{ displayDate(task.deadline) }}</td>
                <td class="text-center">{{ task.priority }}</td>
                <td>
                  <v-container>
                    <v-row class="d-flex" justify="center">
                      <div class="text-xs-center">
                        <v-checkbox v-model="task.isChecked" color="primary"></v-checkbox>
                      </div>
                    </v-row>
                  </v-container>
                </td>
                <td>
                  <v-container>
                    <v-row v-if="!task.isChecked" class="d-flex" justify="center">
                      <div class="text-xs-center mt-2">
                        <AddEditDialogue :taskList="taskList" :inputTitle="task.title" :addDialog="false" class="mb-4" />
                      </div>
                    </v-row>
                    <v-row class="d-flex" justify="center">
                      <div class="text-xs-center mb-2">
                        <DeleteBtn :taskList="taskList" :title="task.title" class="mt-3" />
                      </div>
                    </v-row>
                  </v-container>
                </td>
              </tr>
            </tbody>
          </v-table>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script>
import DeleteBtn from '@/components/DelButtonComponent.vue';
import AddEditDialogue from './AddEditDialogueComponent.vue';
import moment from "moment";

export default {
  components: {
    DeleteBtn,
    AddEditDialogue,
  },
  data() {
    return {
      taskList: [],
    }
  },
  methods: {
    displayDate(date) {
      if (date == "") {
        return "";
      } else {
        return moment(date).format("MM/DD/YYYY");
      }
    }
  }
}
</script>
