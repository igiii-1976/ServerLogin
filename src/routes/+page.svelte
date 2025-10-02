<script>
    import Login from '$lib/components/login.svelte';
</script>

<div class="layout">
    <Login />
</div>

<style>
    :global(body) {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        color: white;
        background-color: #0A0A0A;
    }
    .layout {
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
</style>
