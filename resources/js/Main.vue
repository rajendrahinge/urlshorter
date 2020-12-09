<template>
    <div>
        <app-header />
        <index-component />
        <app-footer />
    </div>
</template>

<script>
    import AppHeader from "./components/Layouts/Header";
    import AppFooter from "./components/Layouts/Footer";
    import IndexComponent from "./pages/IndexComponent";
    export default {

        components : {AppHeader, AppFooter, IndexComponent}

    };
</script>
