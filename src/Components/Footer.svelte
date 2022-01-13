<script>
    export let date=new Date().getFullYear();
</script>


<footer>
    <div class="copyright">&copy; {date} Polls App . Made using <span>SvelteJs</span>
    </div>
</footer>

<style>
    footer {
        text-align: center;
        position: fixed;
        left: 0;
        bottom: 0;
        width: 100%;
    }

    .copyright {
        color: rgb(116, 116, 116);
        font-size: 14px;
        display: inline-block;
        padding: 20px;
        border-top: 1px solid rgb(245, 240, 240);
    }

    span{
        color: royalblue;
        cursor: pointer;
    }
</style>