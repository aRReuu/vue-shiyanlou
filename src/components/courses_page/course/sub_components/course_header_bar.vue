<template>
    <div class="course_header_bar_div" v-if="course_info">
        <!-- 
            title type
            student follow author
         -->
        <div class="course_header_bar_layout_div">
            <div class="course_header_bar_course_info_top">
                <span class="course_header_bar_course_title">{{ course_info.name }}</span>
                <span class="course_type_span"
                :class="course_type_class[course_info.fee_type]">
                    {{ type_dict[course_info.fee_type] }}
                </span>
            </div>
            <div class="course_header_bar_course_info_bottom">
                <span>{{ course_info.students_count }} 人学过</span>
                <span class="span_split">{{ course_info.followers_count }} 人关注</span>
                <span class="span_split">作者: {{ course_info.teacher.name }}</span>
            </div>
        </div>
        
    </div>    
</template>
<script type="text/javascript">
import { mapState } from 'vuex'

export default {
    data () {
        return {
            course_type_class: {
                'free': 'free_course_p',
                'member': 'vip_course_p',
                'bootcamp': 'training_course_p',
                '': ''
            },
            type_dict: {
                'free': '免费',
                'member': '会员',
                'bootcamp': '训练营'
            } 
        }
    },
    computed: {
        ...mapState({
            course_info: state => state.course.course_information
        })
    }
}    
</script>
<style type="text/css" scoped>
/* course_type css设计 */
.course_type_span {
    display: inline-block;
    line-height: 1.6;
    color: #fff;
    padding: 0 6px;
    border-radius: 73px;
    font-size: 13px;
    margin-left: 8px;
}

.free_course_p {
    background: #80c269;
}

.training_course_p {
    background: #f66e6e;
}

.vip_course_p {
    background: #ffae0f;
}

/*  */
.course_header_bar_div {
    width: 100%;
    /*height: 72px;*/
    background: #085441;
    padding: 6px 0 0 30px;
    color: #fff;
    transition: opacity 1s;
    z-index: 8;
}

.course_header_bar_layout_div {
    width: 1170px;
    margin: auto;
}

.course_header_bar_course_title {
    font-size: 22px;
    line-height: 1.6;
    font-weight: 500;
}

.course_header_bar_course_info_bottom {
    font-size: 14px;
}

.span_split:before {
    content: "";
    background: #eee;
    width: 1px;
    height: 20px;
    display: inline-block;
    margin: 0 8px -4px 4px;    
}
</style>
