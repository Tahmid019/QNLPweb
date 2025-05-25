<script lang="ts">
    import profileImage from '$lib/imgs/profile1.jpeg';
    export let link: string = '/';
    export let name: string = 'Name';
    export let designation: string = 'Designation';
</script>

<div class="relative mt-8 flex items-center  gap-x-4">
    <img
        src={profileImage}
        alt={name}
        class="h-10 w-10 rounded-full bg-gray-50"
    />
    <div class="leading-5 text-sm md:text-base lg:text-md xl:text-lg">
        <p class="font-semibold text-white">
        <a href={link}>
            <span class="absolute inset-0"></span>
            {name}
        </a>
        </p>
        <p class="text-gray-500">{designation}</p>
    </div>
</div>