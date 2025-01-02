<script lang="ts">
    let props = $props();
</script>

<div class="footer">
    © illumfx | {props.currentYear}
</div>

<style>
    .footer {
        position: fixed;
        bottom: 0;
    }
</style>