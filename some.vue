<script setup lang="ts">
// 更新状态
const handleUpdateStatus = (id: string, ops: string) => {
    updateTaskStatusAPI({
        id,
        ops: ops === 'ENABLED' ? 'disable' : 'enable'
    }).then(res => {
        if (res.status === 2000) {
            something()
        }
    })
}

const rules = reactive({
    task_img: [
        {
            required: true,
            // 自定义规则
            validator: (rule: any, value: any, callback: any) => {
                if (upload.value._imageUrl) {
                    callback()
                } else {
                    callback(new Error('请上传任务图片'))
                }
            }
        },
    ]
}
</script>
