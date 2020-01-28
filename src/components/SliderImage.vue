<template>
    <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
        <div class="carousel-inner">
            <div class="carousel-item active">
                <img src="https://picsum.photos/1440/350/?random=1" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=2" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=3" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=4" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=5" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=6" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=7" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=8" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=9" class="img-fluid">
            </div>
            <div class="carousel-item">
                <img src="https://picsum.photos/1440/350/?random=10" class="img-fluid">
            </div>
        </div>
        <ol class="carousel-indicators">
            <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="3"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="4"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="5"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="6"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="7"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="8"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="9"></li>
        </ol>
    </div>
</template>

<script>
export default {
    name: 'SliderImage'
}
</script>
<style scoped>
.carousel-indicators{
    position: relative !important;
    margin-top: 40px;
}
.carousel-indicators > li {
    background-color: #e5e5e5;
    border-radius: 50%;
    margin: 0 10px 0 10px;
    width: 10px;
    height: 10px;
}
.active{
    background-color: #000000 !important;
}
</style>