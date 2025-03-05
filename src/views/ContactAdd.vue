<template>
    <div class="page">
        <h4>Thêm mới Liên hệ</h4>
        <ContactAddForm :contact="null" @submit:contact="addContact" />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactAddForm from "@/components/ContactAddForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactAddForm,
    },
    data() {
        return {
            message: "",
        };
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được thêm mới thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>