<template>
  <div >
    <v-container grid-list-xl fluid>
      <v-layout row wrap>
        <!-- mini statistic start -->
        <v-flex lg3 sm6 xs12>
          <mini-statistic
            icon="group"
            title="100+"
            sub-title="Likes"
            color="indigo"      
          >
          </mini-statistic>  
        </v-flex>
        <v-flex lg3 sm6 xs12>
          <mini-statistic
            icon="person_add"
            title="150+"
            sub-title="Connections"
            color="red"      
          >
          </mini-statistic>           
        </v-flex>          
        <v-flex lg3 sm6 xs12>
          <mini-statistic
            icon="person"
            title="200+"
            sub-title="Followers"
            color="light-blue"      
          >
          </mini-statistic>            
        </v-flex>
        <v-flex lg3 sm6 xs12>
          <mini-statistic
            icon="group_add"
            title="50+"
            sub-title="Shots"
            color="purple"      
          >
          </mini-statistic>             
        </v-flex>
        <v-flex lg4 sm12 xs12>
          <profile-card>
          </profile-card>
        </v-flex>
        <v-flex lg4 sm12 xs12>
          <linear-statistic 
            title="Sales"
            sub-title="Sales increase"
            icon="trending_up"
            color="success"
            :value="15"
          >
          </linear-statistic>
          <linear-statistic class="my-4"
            title="Orders"
            sub-title="Increase"
            icon="trending_up"
            color="pink"
            :value="30"
          >
          </linear-statistic>          
          <linear-statistic class="my-4"
            title="Revenue"
            sub-title="Revenue increase"
            icon="trending_up"
            color="primary"
            :value="50"
          >
          </linear-statistic>          
          <linear-statistic class="mt-4"
            title="Cost"
            sub-title="Cost reduce"
            icon="trending_down"
            color="orange"
            :value="25"
          >
          </linear-statistic>          
        </v-flex>
        <v-flex lg4 sm12 xs12>
          <profile-card>
          </profile-card>
        </v-flex>
        <v-flex lg4 sm12 xs12 v-for="(item,index) in trending" :key="'c-trending'+index">
          <circle-statistic
            :title="item.subheading"
            :sub-title="item.headline"
            :caption="item.caption"
            :icon="item.icon.label"
            :color="item.linear.color"
            :value="item.linear.value"
          >
          </circle-statistic>            
        </v-flex>
        <v-flex lg6 sm12 xs12>
          <v-widget title="Activities" contentBg="white">
            <div slot="widget-content">
              <ol class="timeline timeline-activity timeline-point-sm timeline-content-right">
                <li class="timeline-block" v-for="item in activity">
                  <div class="timeline-point">
                    <v-circle dot large :color="item.color"></v-circle>
                  </div>
                  <div class="timeline-content">
                    <time datetime="2018" class="subheading">{{item.timeString}}</time>
                    <div class="py-2 text--secondary" v-html="item.text"></div>
                  </div>
                </li>
              </ol>              
            </div>
          </v-widget>          
        </v-flex>
        <v-flex lg12 sm12 xs12>
          <Table></Table>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
<script>
  import MiniStatistic from '~/components/statistic/MiniStatistic.vue'
  import ProfileCard from '~/components/statistic/card/ProfileCard.vue'
  import LinearStatistic from '~/components/statistic/LinearStatistic.vue'
  import CircleStatistic from '~/components/statistic/CircleStatistic.vue'
  import VCircle from '~/components/circle/VCircle'
  import VWidget from '~/components/VWidget'
  import Table from '~/components/Table'
  export default {
    components: {
      MiniStatistic,
      ProfileCard,
      LinearStatistic,
      CircleStatistic,
      VCircle,
      VWidget,
      Table
    },
    data: () => ({
      trending: [
        {
          subheading: 'Email',
          headline: '15+',
          caption: 'email opens',
          percent: 15,
          icon: {
            label: 'email',
            color: 'info'
          },
          linear: {
            value: 15,
            color: 'info'
          }
        },
        {
          subheading: 'Tasks',
          headline: '90%',
          caption: 'tasks completed.',
          percent: 90,
          icon: {
            label: 'list',
            color: 'primary'
          },
          linear: {
            value: 90,
            color: 'success'
          }
        },
        {
          subheading: 'Issues',
          headline: '100%',
          caption: 'issues fixed.',
          percent: 100,
          icon: {
            label: 'bug_report',
            color: 'primary'
          },
          linear: {
            value: 100,
            color: 'error'
          }
        }
      ],
      activity: [
        {
          avatar: 'https://s3.amazonaws.com/uifaces/faces/twitter/ludwiczakpawel/128.jpg',
          timeString: 'Just now',
          color: 'primary',
          text: 'Michael finished  one task just now.'
        },
        {
          avatar: 'https://s3.amazonaws.com/uifaces/faces/twitter/suprb/128.jpg',
          timeString: '30 min ago',
          color: 'teal',
          text: 'Jim created a new  task.'
        },
        {
          avatar: 'https://s3.amazonaws.com/uifaces/faces/twitter/suprb/128.jpg',
          timeString: '1 hour ago',
          color: 'indigo',
          text: 'Li completed the PSD to html convert.'
        },
        {
          avatar: 'https://s3.amazonaws.com/uifaces/faces/twitter/suprb/128.jpg',
          timeString: '3 hour ago',
          color: 'pink',
          text: 'Michael upload a new pic.'
        },
        {
          avatar: 'https://s3.amazonaws.com/uifaces/faces/twitter/suprb/128.jpg',
          timeString: '10 min ago',
          color: 'cyan',
          text: 'Li assigned a a task to Michael'
        }
      ]
    })
  }
</script>
<style scoped>
  timeline {
    position: relative;
    list-style: none;
    padding-left: 0;
    z-index: 1;
}
ol {
    display: block;
    list-style-type: decimal;
    -webkit-margin-before: 1em;
    -webkit-margin-after: 1em;
    -webkit-margin-start: 0px;
    -webkit-margin-end: 0px;
    -webkit-padding-start: 40px;
}
.timeline-block {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
}
.timeline-point-sm .timeline-point {
    width: 64px;
}
.timeline-point {
    position: relative;
    -ms-flex-negative: 0;
    flex-shrink: 0;
    -webkit-box-flex: 0;
    -ms-flex-positive: 0;
    flex-grow: 0;
    -webkit-box-ordinal-group: 3;
    -ms-flex-order: 2;
    order: 2;
    width: 96px;
    padding-bottom: 30px;
    text-align: center;
}
.timeline.timeline-content-right .timeline-block .timeline-content {
    -webkit-box-ordinal-group: 4;
    -ms-flex-order: 3;
    order: 3;
}
</style>