<template>
  <div class="hello">
    <div class="header">
      <img src="../../static/car.jpg" alt="">
      <div class="personal">
        <span>张小六</span>
        <img src="../../static/car.jpg" alt="">
      </div>
    </div>
    <div class="friend">
      <div class="friendOne" v-for="(item,index) in trends" :key="index">
          <img :src="item.head" alt="">
          <div style="padding-left:15px;">
            <div class="friendOne-right">
              <p>{{item.username}}</p>
              <p>{{item.content}}</p>
            </div>
            <a href="https://www.baidu.com">
              <div class="friendOne-c" @click="gocontent()">
                <img :src="item.trendimg" alt="">
                <span>{{item.trendcontent}}</span>
              </div>
            </a>
           
            <div class="friendOne-parise">
              <div class="pariseOne" @click="parise(index)">
                <img src="../../static/parise.png" alt=""><span>{{item.parisenum}}</span>
              </div>
              <div class="pariseOne">
                <img src="../../static/commment.png" alt=""><span>评论</span>
              </div>
              <div class="pariseOne" v-if="item.isself == 0">
                <img src="../../static/delete.png" alt=""><span>删除</span>
              </div>
            </div>
            <div class="time">{{item.time}}</div>
            <div class="comment" v-for="(items,idx) in item.commentList" :key="idx">
              <div v-if="idx<num">
                <span style="color:#5bafff;">{{items.commentname}}</span>：<span>{{items.commentcontent}}</span>
              </div>
            </div>
            <div v-if="num <= 3" @click="getMorecomment()">查看全部评论</div>
            <div v-if="num > 3" @click="getLesscomment()">收起评论</div>          
          </div>
          
      </div>
    </div>
    
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      num:"3",
      commentlist:[],
      trends:[
        {
          isself:1,
          head:"../../static/car.jpg",
          username:"零度",
          content:"滴滴出行，出行无忧。",
          trendimg:"../../static/car.jpg",
          trendcontent:"滴滴出行，从此出行无忧。",
          parisenum:9,
          parisestate:0,
          time:"1小时前",
          commentList:[
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
            {
              commentname:"秋香",
              commentcontent:"赞~"
            },
          ]
        }
      ],
      
    }
  },
  mounted(){
  
  },
  methods:{
    gocontent(){
      Navigator
    },
    getMorecomment(){
      var that = this;
      that.num = 50;
      console.log(that.num);
    },
    getLesscomment(){
      var that = this;
      that.num = 3;
      console.log(that.num); 
    },
    parise(index){
      var that = this;
        console.log(that.trends[index]);

      if(that.trends[index].parisestate == 0){
        that.trends[index].parisenum = that.trends[index].parisenum-1;
        that.trends[index].parisestate = 1;
        console.log(that.trends[index].parisestate);

      }else{
        that.trends[index].parisenum = that.trends[index].parisenum+1;
        that.trends[index].parisestate = 0;
        console.log(that.trends[index].parisestate);
      }
    }
  }
}
</script>
<style scoped>

.hello {
 width: 100%;
}
.header{
  position: relative;
}
.header img{
  width: 100%;
}
.header .personal {
  position: absolute;
  right: 0;
  bottom: 10px;
}
.header .personal > span {
  position: relative;
  right: 70px;
  bottom: -30px;
  color: #ffffff;
  font-size: 18px;
}
.header .personal img{
  width:  48px;
  height: 48px;
}
.friend{
  width: 100%;
}
.friendOne{
  display: flex;
  padding: 16px;
  border: 1px solid #eeeeee;
}

.friendOne-right{
  padding-bottom: 4px;
}
.friendOne-right p:nth-child(1){
  font-size: 15px;
  color: #41454d;
  font-weight: bold;
}
.friendOne img:nth-of-type(1){
  width: 40px;
  height: 40px;
}
.friendOne-c{
  display: flex;
  padding: 10px;
  align-items: center;
  background: #eeeeee;
}
.friendOne-c > span{
  padding-left: 10px;
}
.friendOne-parise{
  display: flex;
  /* line-height: 60px; */
}
.friendOne-parise .pariseOne{
  display: flex;
  align-items: center;
  margin-right: 15px;
  padding: 10px 0;
}
.friendOne-parise .pariseOne span{
  margin-left: 5px;
}
.friendOne-parise .pariseOne img{
  width: 17px;
  height: 17px;
}
.time{
  padding: 10px 0;
  font-size: 12px;
  color: #acb1b7;
}
</style>
