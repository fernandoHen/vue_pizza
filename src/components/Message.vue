<template>
    <div class="message-container">
        <p>{{msg}}</p>
    </div>
</template>

<script>
export default {
    name: "message",
    props: {
        msg: String
    }
}
</script>

<style scoped>
    .message-container {
        border-radius: 5px;
        text-align: center;
        padding: 10px;/*espaço interno */
        max-width: 400px;
        margin: 30px auto;

        background: #dbead5;
        border: 1px solid #93bf85;
        color: #26652D;
        background-image: url('/public/img/icon-success.png');
        background-repeat: no-repeat;
        background-position: 16px center;
        background-size: 26px;

    }

.msg-alert-warning {
    border: 1px solid #F0CD9D;
    background: #FDF8E2;
    color: #C89844;
    background-image: url('/public/img/icon-alert.png');
    background-repeat: no-repeat;
    background-position: 16px center;
}

.msg-alert-info {
    background: #DAEEF9;
    border: 1px solid #BEDDF1;
    color: #5694B9;
    background-image: url('/public/img/icon-info.png');
    background-repeat: no-repeat;
    background-position: 16px center;
}

.msg-alert-error {
    background: #f9f2f4;
    border: 1px solid #FBB7B4;
    color: #D46760;
    background-image: url('/public/img/icon-error.png');
    background-repeat: no-repeat;
    background-position: 16px center;
}



</style>
