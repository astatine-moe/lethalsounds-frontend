<script>
    import { sounds } from "$lib/client/stores/preferences";
    import { Keys } from "$lib/client/util/sounds";

    export let text;
    export let checked;
    export let onChange = () => {};
</script>

<div>
    <label class="relative inline-flex items-center cursor-pointer">
        <input
            type="checkbox"
            value=""
            class="sr-only peer"
            bind:checked
            on:change={() => {
                if ($sounds) {
                    Keys[Math.floor(Math.random() * Keys.length)].play();
                }
                onChange();
            }}
        />
        <div
            class="w-11 h-6 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-800 rounded-none peer bg-temptress-600 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-none after:h-5 after:w-5 after:transition-all border-gray-600 peer-checked:bg-trinidad-500"
        ></div>
        <span class="ms-3 text-sm font-medium text-gray-900 dark:text-gray-300"
            ><slot /></span
        ></label
    >
</div>
