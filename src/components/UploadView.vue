<script>
import UploadForm from '@/components/UploadForm.vue'
export default {
    data() {
        return {
            message: "UploadPhoto"
        };
    },
    components: { UploadForm }
}
</script>








resolve: {
…
},
server: {
 proxy: {
 '^/api*': {
 target: 'http://localhost:8080/'
 }
 }
}