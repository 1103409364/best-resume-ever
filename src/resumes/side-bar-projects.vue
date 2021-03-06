<template>
  <div id="resume2" class="resume">
    <div class="triangle"></div>
    <div class="triangle-bottom"></div>
    <div class="main">
      <div class="top-row">
        <span class="person-name"> {{ person.name.first + person.name.last }} </span>
        <span class="person-position"> {{ person.position }} </span>
        <span class="sal person-position">{{ person.sal }}</span>
      </div>
      <div class="left-col">
        <!-- <div class="person-image">
          <div class="image-centerer">
            <div class="img"></div>
          </div>
        </div> -->
        <div class="about">
          <h3 class="about">{{ lang.about }}</h3>
          <div class="birth">{{ person.sex }}</div>
          <div class="birth">{{ person.birth.year }}</div>
          <div class="birth">{{ person.nation }}</div>
          <div class="location">{{ person.birth.location }}</div>
          <div class="location">{{ person.birth.educational }}</div>
        </div>
        <!-- 联系方式 -->
        <div class="contact">
          <h3>{{ lang.contact }}</h3>
          <div class="contact-row">
            <a href="'tel:'+person.contact.phone">{{ person.contact.phone }}</a>
          </div>
          <div class="contact-row">
            <a :href="'mailto:' + person.contact.email">{{ person.contact.email }}</a>
          </div>
          <div class="contact-row">
            {{ person.contact.street }} <br />
            {{ person.contact.city }}
          </div>
          <!-- <div class="contact-row">
          <a :href="'https://github.com/' + person.contact.github">
            https://github.com/{{ person.contact.github }}
          </a>
        </div> -->
        </div>
        <!-- 教育经历 -->
        <div class="education">
          <h3>{{ lang.education }}</h3>
          <div class="education-block" v-for="(education, i) in person.education" :key="i">
            <div class="row">
              <span class="degree">{{ education.timeperiod }}</span>
            </div>
            <div class="row">
              <span class="degree-description">{{ education.description }}</span>
            </div>
            <div class="row">
              <span class="degree">{{ education.degree }}</span>
            </div>
          </div>
        </div>
        <!-- 职业技能 -->
        <div class="skills-block">
          <h3>{{ lang.skills }}</h3>
          <div class="skills">
            <div class="skill" v-for="(skill, i) in person.skills" :key="i">
              <span class="skill-name">{{ skill.name }}</span>
            </div>
          </div>
          <span class="skills-other"> {{ person.skillDescription }} </span>
        </div>
        <!-- 职业技能 -->
        <div class="skills-block">
          <h3>{{ lang.otherSkills }}</h3>
          <div class="skills">
            <div class="skill" v-for="(skill, i) in person.otherSkills" :key="i">
              <span class="skill-name">{{ skill.name }}</span>
            </div>
          </div>
          <span class="skills-other"> {{ person.skillDescription }} </span>
        </div>
      </div>

      <div class="right-col">
        <div class="experience">
          <h3>{{ lang.experience }}</h3>
          <div class="experience-block" v-for="(experience, i) in person.experience" :key="i">
            <div class="row">
              <span class="company"> {{ experience.company }} -</span>
              <span class="job-title"> {{ experience.position }} </span>
            </div>
            <div class="row">
              <span class="time-period"> {{ experience.timeperiod }}</span>
            </div>
            <div class="row">
              <span class="job-description"> {{ experience.description }} </span>
            </div>
          </div>
        </div>
        <div class="projects">
          <h3>{{ lang.projects }}</h3>
          <div class="project-block" v-for="(project, i) in person.projects" :key="i">
            <div class="row">
              <span class="name"> {{ project.name }} </span>
              <span class="platform">{{ project.platform }}</span>
              <div class="row project-item">
                <!-- <div class="label">项目时间：</div> -->
                <div class="time-period color-info">{{ project.timeperiod }}</div>
              </div>
              <div class="row project-item">
                <div class="label">项目简介：</div>
                <div class="description color-info">{{ project.description }}</div>
              </div>
              <div class="row project-item" v-if="project.duty">
                <div class="label">我的职责：</div>
                <div class="duty color-info">{{ project.duty }}</div>
              </div>
              <div class="row project-item" v-if="project.result">
                <div class="label">项目成果：</div>
                <div class="description color-info">{{ project.result }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'side-bar-projects';
export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
@color1: #3e75b7;
@color2: #006064;

#resume2 {
  height: 57.75cm;
  // font-family: 'Raleway', sans-serif;
  // font-family: 'Microsoft Yahei light', sans-serif;
  font-family: 'Open Sans';
  padding-bottom: 60px;
  color: #606266;
  a,
  a:focus,
  a:hover,
  a:visited {
    text-decoration: none;
  }
  h3 {
    text-transform: uppercase;
    // padding-top: 0;
    // margin-top: 0;
    letter-spacing: 5px;
    font-weight: 400;
    color: @color1;
    // text-decoration: underline;
  }
  .color-info {
    color: #82848a;
  }
  .triangle {
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 280px 0px 200px 380px;
    border-color: @color1 transparent transparent transparent;
    position: absolute;
    // left: -600px;
    right: 0;
    top: 0;
    z-index: 0;
  }
  .triangle-bottom {
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 200px 380px 280px 0px;
    border-color: transparent transparent @color1 transparent;
    position: absolute;
    // left: -600px;
    left: 0;
    bottom: -30px;
    z-index: 0;
  }
  .main {
    position: relative;
    z-index: 1;
  }
  .top-row {
    width: 26%;
    padding-left: 8%;
    padding-right: 4%;
    padding-top: 30px;
    padding-bottom: 10px;
    // background-color:@color2;
    position: relative;
    z-index: 1;
    // color: #fff;
    span {
      width: 100%;
      display: block;
      text-align: right;
      font-weight: normal;
    }
    span.person-name {
      text-transform: uppercase;
      font-size: 40px;
      letter-spacing: 2px;
    }
    span.person-position {
      letter-spacing: 2px;
    }
  }
  .left-col {
    width: 26%;
    float: left;
    margin-left: 8%;
    padding-right: 2%;
    padding-bottom: 30px;
    text-align: right;
    position: relative;
    // top: -148px;
    // background-color: #dfe0e2;
    // color: @main-color;
    // border-top: 1px solid @color1;
    h3 {
      margin-top: 20px;
      margin-bottom: 10px;
      // color: @accent-color;
      // color: #fff;
      // &:nth-of-type(1) {
      //   margin-top: 0;
      // }
    }
    .person-image .image-centerer {
      display: flex;
      justify-content: center;
      height: auto;
      overflow: hidden;
      .img {
        flex: none;
        background: url('../../resume/id.jpg');
        background-position: center;
        background-size: cover;
        height: 250px;
        width: 100%;
      }
    }
    .contact .contact-row {
      letter-spacing: 2px;
      // margin-bottom: 3px;
      a {
        color: #606266;
      }
    }
    // .contact .contact-row:first-of-type {
    //   margin-top: 10px;
    // }
    // .contact .contact-row:last-of-type {
    //   margin-bottom: 20px;
    // }
    // .contact .contact-row.dots {
    //   margin-top: 20px;
    //   margin-bottom: 15px;
    //   font-size: 10px;
    //   color: rgba(153, 153, 153, 0.6);
    // }
    .skills-block {
      span.skill-name {
        letter-spacing: 2px;
      }
    }
  }
  .right-col {
    width: 53.85%;
    float: right;
    padding-left: 2%;
    padding-right: 8%;
    // border-top: 1px solid @color1;
    border-left: 1px solid @color1;
    padding-bottom: 30px;
    h3 {
      // color: @main-color;
      margin-top: 20px;
      margin-bottom: 10px;
      // &:nth-of-type(1) {
      //   margin-top: 0;
      // }
    }
    .experience-block {
      margin-bottom: 10px;
      line-height: 1.5;
      .row:first-child {
        margin-bottom: 3px;
      }
      .row .company {
        text-transform: uppercase;
        font-weight: bold;
      }
      .row .job-title {
        color: #82848a;
      }
      .row .time-period {
        color: #82848a;
      }
      .row .job-description {
        color: #82848a;
      }
    }
    .projects {
      // margin-top: 50px;
      .project-block {
        margin-bottom: 10px;
        line-height: 1.5;
        .degree {
          font-size: 14px;
          text-transform: uppercase;
          margin-bottom: 3px;
        }
        .name {
          font-weight: bold;
        }
        .project-item {
          display: flex;
          .label {
            min-width: 80px;
          }
        }
        .platform {
          padding: 2px 6px 4px 6px;
          margin-left: 10px;
          background-color: #ecf5ff; //@color1;
          color: @color1;
          border-radius: 50px;
          font-size: 12px;
          line-height: 20px;
        }
      }
    }
    // .education {
    //   margin-top: 50px;
    //   .education-block {
    //     margin-bottom: 10px;
    //     .degree {
    //       font-size: 12px;
    //       text-transform: uppercase;
    //       margin-bottom: 3px;
    //     }
    //   }
    // }
  }
}
</style>
