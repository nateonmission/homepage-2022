<template>
  <div class="resume">
    <q-expansion-item
      class="resume_header shadow-3 overflow-hidden"
      icon="psychology"
      label="Skills"
      header-class="text-dark "
      expand-icon-class="text-dark"
    >
      <q-card>
        <q-card-section class="resume_content">
          <div class="col_container">
            <div class="column">
              <ul class="normal resume_text">
                <li class="normal resume_text">
                  Python
                  <ul class="normal resume_text">
                    <li class="normal resume_text">Python</li>
                    <li class="normal resume_text">Java</li>
                    <li class="normal resume_text">JavaScript</li>
                    <li class="normal resume_text">Vue</li>
                  </ul>
                </li>
                <li class="normal resume_text">Java</li>
                <li class="normal resume_text">JavaScript</li>
                <li class="normal resume_text">Vue</li>
              </ul>
            </div>
            <div class="column">
              <ul class="normal resume_text">
                <li class="normal resume_text">
                  Python
                  <ul class="normal resume_text">
                    <li class="normal resume_text">Python</li>
                    <li class="normal resume_text">Java</li>
                    <li class="normal resume_text">JavaScript</li>
                    <li class="normal resume_text">Vue</li>
                  </ul>
                </li>
                <li class="normal resume_text">Java</li>
                <li class="normal resume_text">JavaScript</li>
                <li class="normal resume_text">Vue</li>
              </ul>
            </div>
          </div>
        </q-card-section>
      </q-card>
    </q-expansion-item>

    <q-expansion-item
      class="resume_header shadow-3 overflow-hidden"
      icon="engineering"
      label="Experience"
      header-class="resume_header-inner text-dark"
      expand-icon-class="text-dark"
    >
      <q-card class="">
        <q-card-section class="resume_content">
          <p class="normal resume_text">
            EXP -Python, Java, JavaScript, Vue, Angular, C#
          </p>
        </q-card-section>
      </q-card>
    </q-expansion-item>

    <q-expansion-item
      class="resume_header shadow-3 overflow-hidden"
      icon="verified"
      label="Certifications"
      header-class="resume_header-inner text-dark"
      expand-icon-class="text-dark"
    >
      <q-card>
        <q-card-section class="resume_content">
          <p class="normal resume_text">
            Python, Java, JavaScript, Vue, Angular, C#
          </p>
        </q-card-section>
      </q-card>
    </q-expansion-item>

    <q-expansion-item
      class="resume_header shadow-3 overflow-hidden"
      icon="school"
      label="Education"
      header-class="resume_header-inner text-dark"
      expand-icon-class="text-dark"
    >
      <q-card>
        <q-card-section class="resume_content">
          <ul>
            <li
              v-for="(item, index) in resume['jerome']['education']"
              :key="`item-${index}`"
            >
              <span class="normal">
                {{ item["institution"] }}
              </span>
              <span class="text_italic"> ({{ item["location"] }}) </span>
              <ul class="resume_content">
                <li v-if="resume['jerome']['isUniversity']">
                  <span class="text_normal">
                    {{ item["credential"]["title"] }}
                  </span>
                  <ul>
                    <li
                      v-for="(major, index) in item['credential'][
                        'specialization'
                      ]"
                      :key="`item-${index}`"
                    >
                      {{ major }}
                    </li>
                  </ul>
                </li>
                <li v-else>
                  <span class="text_normal">
                    {{ item["credential"]["title"] }}
                  </span>
                </li>
                <li v-if="!item['dateCompleted' == '']">
                  <span class="text_normal">
                    Awarded: {{ item["dateCompleted"] }}
                  </span>
                </li>
              </ul>
            </li>
          </ul>
        </q-card-section>
      </q-card>
    </q-expansion-item>

    <q-expansion-item
      class="resume_header shadow-3 overflow-hidden"
      icon="computer"
      label="Projects"
      header-class="resume_header-inner text-dark"
      expand-icon-class="text-dark"
    >
      <q-card>
        <q-card-section class="resume_content">
          <p class="normal resume_text">
            Python, Java, JavaScript, Vue, Angular, C#
          </p>
        </q-card-section>
      </q-card>
    </q-expansion-item>
  </div>
</template>

<script setup>
// This is where your Javascript goes
// to define your Vue component, which
// can be a Layout, a Page or your own
// component used throughout the app.
</script>

<style>
/* This is where your CSS goes */
</style>
