<!-- <template>
    <div class="score">
        <div class="top">
            <div class="mainTitle">作品评分</div>
        </div>
        <CardMini_admin :key="idx" v-for="(i, idx) in dataList" :title=i.workTitle :auth="i.makerName"
            :avatar=i.makerAvatar :hot=i.views :cover=i.coverFile :status=i.prizeName :score=4.7 @click="$router.push({
            path: 'admin/workDetail',
            query: { workId: i.workId }
        })"></CardMini_admin>
        <div :class="isSafari ? 'footer' : ''"></div>
    </div>
</template>

<script>
    import { getScoreWorks } from "@/api/score"
    export default {
        name: "Score",
        props: {
        },
        data() {
            return {
                byEnd: false,
                pageNum: 1,
                pageSize: 10,
                loading: false,
                isSafari: true,
                dataList: [],

            }
        },
        watch: {
            // byEnd(to) {
            //     if (to) {
            //         console.log(11)
            //         if (!this.loading) {
            //             this.loading = true
            //             // loadmore here
            //             getScoreWorks({
            //                 contestId: this.globalData.contestId,
            //                 pageNum: this.pageNum,
            //                 pageSize: this.pageSize,
            //             }).then(v => {
            //                 console.log(v)
            //                 if (!v.code) {
            //                     this.dataList = this.dataList.concat(v.data)
            //                     v.data.forEach(ele => {
            //                         this.replaceBlob(ele, ['coverFile'])
            //                     });
            //                     this.pageNum++;
            //                 }
            //                 this.loading = false
            //             })
            //         }
            //     }
            // },
        },
        methods: {
            replaceBlob(tarObject, attrList) {
                console.log(attrList)
                attrList.forEach(attr => {
                    getSrc(tarObject[attr]).then(v => {
                        // console.log(v)
                        tarObject[attr] = v
                        this.$forceUpdate()
                    })
                    // .catch(err => {
                    //     ElMessage.error('图片加载失败')
                    // })
                    tarObject[attr] = pubuse('loading.gif')
                    // console.log(this.dataList)
                });
            },
            scroll(e) {
                // console.log(e)
                let a = e.target.scrollTop
                this.catchTop = a
                let b = e.target.offsetHeight
                let c = e.target.scrollHeight
                let d = c - b - a
                // console.log(d)
                if (d < 140) {
                    this.byEnd = true
                } else {
                    this.byEnd = false
                }
            },
        },
        mounted() {
            this.loading = true
            getScoreWorks({
                contestId: this.globalData.contestId,
                // pageNum: this.pageNum,
                // pageSize: this.pageSize,
            }).then(v => {
                console.log(v)
                if (!v.code) {
                    this.dataList = v.data
                    v.data.forEach(ele => {
                        this.replaceBlob(ele, ['coverFile'])
                    });
                    this.pageNum++;
                }
                this.loading = false
            })
            this.isSafari = isSafari()
        },
    }
</script>


<style scoped>
    .top {
        height: 85px;
        width: 100%;
        display: flex;
        flex-direction: row;
    }

    .mainTitle {
        margin-left: 20px;
        margin-top: 20px;
        font-size: 32px;
        color: #000;
        font-weight: 500;
        height: 45px;
        /* width: 128px; */
    }

    .footer {
        height: 100px;
    }
</style> -->