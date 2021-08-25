<template>
    <div class="container">
        <header>NWA Coders</header>
        <h1>About Us</h1>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Recusandae maxime officia, odit ipsa explicabo quibusdam, autem nulla corporis veritatis eum commodi eveniet laboriosam blanditiis? Eum beatae minus fuga doloremque consectetur.</p>
        <h2>Where We Came From</h2>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Maxime autem voluptate consectetur facere quos, quod dolorem aliquam odio pariatur id earum a quibusdam nemo asperiores qui consequatur modi! Ullam, maxime.</p>
        <h2>Where We're Going</h2>
        <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vel, deleniti, provident distinctio inventore assumenda ab cupiditate obcaecati odit ducimus dicta suscipit adipisci doloremque. Quae asperiores corporis quidem magnam consectetur. Eos.</p>
        <h2>Mission Statement</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Facere in officiis facilis? Labore adipisci, nam soluta molestiae quas possimus corporis, ex tempora velit neque quasi eligendi ullam reprehenderit nemo maiores.</p>
        <h2>Community Leaders</h2>


    </div>
</template>

<script>
export default {
    head() {
        return {
            title:"About Us",
            meta: [
                {
                    hid:"description",
                    name: "description",
                    content: "A community for web developers in Northwest Arkansas"
                }
            ]
        }
    }
}
</script>

<style>
    h1, h2 {
        text-decoration: underline;
    }
    .container {
        background-color: lightblue;
    }
</style>
