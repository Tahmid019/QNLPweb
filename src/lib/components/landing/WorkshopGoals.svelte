<script lang="ts">
	import CloseCard from "../ui/card/CloseCard.svelte";

    let WorkshopGoals_text = "The primary goal of this workshop is to bridge the gap between NLP and Quantum Machine Learning (QML) by introducing participants to the foundational principles, practical tools, and state-of-theart developments in quantum computing applied to NLP tasks. The workshop fosters interdisciplinary knowledge and empowers researchers, practitioners, and students with the skills necessary to explore and prototype hybrid quantum-classical NLP models. The participant benefits after attending this workshop. They got concepts of quantum computing methodology, quantum machine learning, hybrid quantum-classical algorithms, and utilization of quantum machine learning algorithms for NLP tasks.";
    let Audi_text = "This workshop is designed for researchers, graduate students, practitioners, and developers from academia and industry who are interested in the intersection of quantum computing, machine learning, and NLP. We anticipate approximately 40 to 60 participants based on interest trends in previous workshops at the intersection of quantum computing and AI. The hands-on nature of the session may limit the upper bound slightly to ensure productive engagement during practical components";
</script>


<section id="workshop" class="relative mx-auto mt-20 max-w-7xl sm:px-6 text-center md:px-8">
    <div class="container flex flex-col lg:flex-row">
        <div class="cont-a lg:w-[50%] pb-3 lg:pb-0 lg:pr-3">
            <CloseCard title="Workshop Goals" text={WorkshopGoals_text}/>
        </div>
        <div class="cont-b lg:w-[50%] pt-3 lg:pt-0 lg:pl-3">
            <CloseCard title="Audience & Participation" text={Audi_text}/>
        </div>
    </div>
</section>