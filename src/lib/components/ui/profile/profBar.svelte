<script lang="ts">
    import profileImage from '$lib/imgs/profile1.jpeg';
    export let link: string = '/';
    export let name: string = 'Name';
    export let designation: string = 'Designation';
    export let profImg: string = profileImage;
</script>

<div class="relative mt-8 flex flex-row items-center  gap-x-4 shadow-lg md:shadow-xl rounded-lg border p-3">
    <img
    src={profImg}
    alt={name}
    class="h-10 w-10 rounded-full bg-gray-50"
    />
    <div class="leading-5 text-sm md:text-base lg:text-md xl:text-lg">
        <a href={link}>
        <p class="font-semibold text-[var(--black-0)]">
            <span class="absolute inset-0"></span>
            {name}
        </p>
        <p class="text-gray-500">{designation}</p>
    </a>
    </div>
</div>