<template>
    <div class="upload-file-wrapper">
        <div class="upload-area">
            <div class="upload-area-tips">
                <el-icon size="24">
                    <UploadFilled />
                </el-icon>将目录或多个文件拖拽到此进行扫描
            </div>
            <div class="upload-area-tips">支持的文件类型：.jpg、.jpeg .bmp .webp .gif .png</div>
            <div class="upload-area-tips">每个文件允许的最大尺寸为：1M</div>
        </div>
        <div class="upload-btn-group">
            <el-button type="primary" @click="handleChooseFile">选择文件</el-button>
            <el-button type="primary">选择文件夹</el-button>
        </div>
        <el-table :data="tableData" class="upload-file-table">
            <el-table-column fixed prop="fileName" label="文件名" width="150" />
            <el-table-column prop="fileType" label="类型" width="120" />
            <el-table-column prop="fileSize" label="大小" width="120" />
            <el-table-column prop="uploadStatus" label="状态" width="120" />
            <el-table-column fixed="right" label="操作" min-width="120">
                <template #default>
                    <el-button :icon="Delete" size="small" circle />
                </template>
            </el-table-column>
        </el-table>
        <div class="upload-info-btn-group">
            <el-button size="small">文件数量：{{ uploadFilesTotal }}</el-button>
            <el-button size="small">成功上传：{{ successfulFilesTotal }}</el-button>
            <el-button size="small">{{ uploadFilesTotalSize }}字节</el-button>
        </div>
        <el-button :disabled="isDisabled">开始上传</el-button>
    </div>
</template>

<script setup>
import { Delete } from '@element-plus/icons-vue'
import { onMounted, ref } from 'vue';

const uploadFilesTotal = ref(0);
const successfulFilesTotal = ref(0);
const uploadFilesTotalSize = ref(0);
const isDisabled = ref(false);

const tableData = ref([])




// const tableData = [
//     {
//         fileName: 'weerwerw',
//         fileType: 'jpg',
//         fileSize: 'California',
//         uploadStatus: '待上传',
//     },
//     {
//         fileName: 'weerwerw',
//         fileType: 'jpg',
//         fileSize: 'California',
//         uploadStatus: '待上传',
//     }
// ]
</script>


<style lang="scss">
.upload-file-wrapper {
    width: 50%;
    margin: 0 auto;
}

.upload-area {
    padding: 20px;
    font-size: 13px;
    color: #999;
    border: 1px solid #ccc;
    margin-bottom: 15px;

    .upload-area-tips {
        margin-bottom: 20px;
        text-align: center;
    }

    .upload-area-tips:last-child {
        margin-bottom: 0;
    }
}

.upload-file-table {
    margin: 10px;
}

.upload-info-btn-group {
    margin: 10px;
}
</style>