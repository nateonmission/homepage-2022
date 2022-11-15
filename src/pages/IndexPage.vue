<template>
  <q-page class="flex column justify-between" :style-fn="myTweek">
    <div class="wrapper">
      <div class="who">
        <div class="avatarDiv">
          <img
            src="../../public/icons/atom_09.svg"
            alt="gooky starburt"
            class="avatar_icon_left"
          />
          <img
            src="../../public/imgs/nateonmission.jpg"
            alt="Nate On Mission"
            class="avatar"
          />
          <img
            src="../../public/icons/atom_03.svg"
            alt="gooky starburt"
            class="avatar_icon_right"
          />
        </div>
        <div class="name">
          <p class="slackey_emphisis">{{ handle }}</p>
        </div>
        <div class="intro">
          <img src="../../public/icons/atom_12.svg" alt="gookie starburst" />
          <p class="intro normal">
            Hi, my name is Nate Allen and I'm a software developer and
            technologist! I've been playing with computers since I was 8 years
            old, when I got a Commodor64 for Christmas! Over the years, I've
            seen many changes and have enjoyed the ride as technology has
            transformed our World and conventions come and go.
          </p>
        </div>
      </div>

      <div class="resume">
        <q-expansion-item
          class="resume_header shadow-3 overflow-hidden"
          icon="psychology"
          label="Skills"
          header-class="text-dark exp_item"
          expand-icon-class="text-dark"
        >
          <q-card>
            <q-card-section class="resume_content">
              <div class="skillsContainer">
                <div class="skillContainer"
                v-for="(skill, index) in skills"
                :key="`item-${index}`"
                >

                  <Span class="resumeNormal">{{skill['skill']}}</Span>
                  <ul class="subSkill">
                    <li
                    class="normal subSkill"
                    v-for="(sub, index) in skill['subSkills']"
                    :key="`item-${index}`"
                    >
                      <span class="resume">{{sub}}</span>
                    </li>
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

              <p
                class="normal resume_text"
                v-for="(position, index) in experience"
                :key="`item-${index}`"
              >
                <span class="resumeNormal">{{ position["company"] }}</span><br />
                <span class="resume">{{ position["jobTitle"] }}</span><br />
                <span class="resume">{{ position["location"] }}</span><br/>
                <span class="resume">{{ months[position["monthStart"]-1] }} {{ position["yearStart"] }} </span> -
                  <span v-if="!position['isCurrent']" class="resume">{{ months[position["monthEnd"]-1] }} {{ position["yearEnd"] }} </span>
                  <span v-if="position['isCurrent']" class="resume">Present</span>
                  <br/>


                <ul class="resume">
                <li
                  v-for="(desc, index) in position['jobDescription']"
                  :key="`item-${index}`"
                  class="normal"
                ><span class="resume">
                  {{ desc }}<br /></span>
                </li>
              </ul>

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
              <p
                class="normal resume_text"
                v-for="(cert, index) in certs"
                :key="`item-${index}`"
              >
                <span class="resumeNormal">
                  {{ cert["provider"] }}: {{ cert["name"] }}
                  </span><span class="normal">
                  <br />
                  <span class="resume">Achieved: {{ cert["achieved"] }}
                  <br />
                  Expires: {{ cert["expires"] }}</span>
                </span>
              </p>
              <span class="normal">* Validation information upon request</span>
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
              <p
                class="normal resume_text"
                v-for="(inst, index) in edu"
                :key="`item-${index}`"
              >
                <span class="resumeNormal">{{ inst["institution"] }}</span> <br />
                <span class="resume">{{ inst["location"] }}</span>
                <br />
                <span class="resume"
                  >Completed: {{ inst["dateCompleted"] }}</span
                >
                <br />
                <span class="resume">{{ inst["credential"]["title"] }} </span>
                <br />

                <span
                  v-if="inst['credential']['isDegree'] && inst['specializations'].length > 1" class="resume"
                >
                Majors:
                </span>

                <span
                v-if="inst['credential']['isDegree'] && inst['specializations'].length == 1" class="resume"
              >
              Major:
              </span>

                <span v-if="!inst['credential']['isDegree']" class="resume"
                  >Focus of Coursework:
                </span>

                <ul class="resume">
                <li
                  v-for="(special, index) in inst['specializations']"
                  :key="`item-${index}`"
                  class="normal"
                ><span class="resume">
                  {{ special }}<br /></span>
                </li>
              </ul>

              </p>
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

              <p class="normal resume_text"
              v-for="(project, index) in projects"
              :key="`item-${index}`"
              >
                <span class="normal">
                  <a :href=" project['githubLink'] " class="resume">{{ project['title'] }}</a>
                </span><br/>
                <span class="normal"> {{ project['description'] }} </span>
                <ul class="resume">
                  <li
                    v-for="(skill, index) in project['skillsUsed']"
                    :key="`item-${index}`"
                    class="normal"
                  ><span class="resume">
                    {{ skill }}<br /></span>
                  </li>
                </ul>
              </p>

            </q-card-section>
          </q-card>
        </q-expansion-item>

        <q-expansion-item
        class="resume_header shadow-3 overflow-hidden"
        icon="cloud_download"
        label="Downloadables"
        header-class="resume_header-inner text-dark"
        expand-icon-class="text-dark"
      >
        <q-card>
          <q-card-section class="resume_content">

              <span class="normal">
                <a href="#" class="resume">Resume (PDF)</a>  (Updated: October 2022)
                <br/>
                <a href="../../public/data/Resume.json" class="resume">Resume (JSON)</a> (Updated: October 2022)
              </span>

          </q-card-section>
        </q-card>
      </q-expansion-item>

      </div>
    </div>

    <div class="footer">
      <div class="social">
        <a href="https://linkedin/in/nateonmission" target="_blank">
          <img
            src="../../public/icons/linkedin.svg"
            alt="linked in"
            class="social"
          />
        </a>

        <a href="https://github.com/nateonmission" target="_blank">
          <img
            src="../../public/icons/github.svg"
            alt="github"
            class="social"
          />
        </a>

        <a href="https://twitter.com/nateonmission" target="_blank">
          <img
            src="../../public/icons/twitter.svg"
            alt="twitter"
            class="social"
          />
        </a>
      </div>

      <div class="copyright">
        <p class="copyright">&#169;&nbsp;{{ new Date().getFullYear() }}</p><p class="copyright">J.&nbsp;Nathan&nbsp;Allen</p>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import resume from "../../public/data/Resume.json";
export default defineComponent({
  props: ["handle"],
  methods: {
    myTweak() {
      // "offset" is a Number (pixels) that refers to the total
      // height of header + footer that occupies on screen,
      // based on the QLayout "view" prop configuration

      // this is actually what the default style-fn does in Quasar
      return { minHeight: "500px" };
    },
  },

  data() {
    return {
      resume: resume,
      edu: resume["jerome"]["education"],
      certs: resume["jerome"]["certifications"],
      skills: resume["jerome"]["skills"],
      experience: resume["jerome"]["experience"],
      projects:  resume["jerome"]["projects"],
      months: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
    };
  },
});
</script>
