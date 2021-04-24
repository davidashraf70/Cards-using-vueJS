<template>
    <div class="product">
        <div :class="'product-inner  ' + product.color">
            <div class="product-text-wrap">
                <h2 class="bg-text">{{product.bgtext}}</h2>
            </div>
            <div class="product-image-wrap">
                <img :src="product.src" class="image">
            </div>
            <div class="product-detail">
                <h2>{{product.title}}</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium vel, quae dolores vitae aspernatur illo et corrupti? Laboriosam, quo aperiam!</p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"product",
    props:['product']
}
</script>
<style lang="scss" scoped>
.product{
    flex: 1 1 33.333%;
    width: 100%;
    padding: 25px;
    .product-inner{
        position: relative;
        padding: 25px;
        box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
        perspective: 1000px;
        // border: 5px solid black;    
        .product-image-wrap{
            position: relative;
            z-index: 1;
            transform-origin: center;
            .image{
                width: 100%;
                filter: drop-shadow(0px 0px 12px rgba(0,0,0,0.25));
            }
        }
        .product-text-wrap{
            position: absolute;
            top: -120px;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: 0;
            overflow: hidden;
            perspective: 1000px;
            h2{
                color: #313131;
                font-size: 128px;
                font-weight: 900;
                opacity: 0.2;
                transform-origin: center;
            }
        }
        .product-detail{
            background-color: #fff;
            padding: 25px;
            margin: 20px -25px -25px;
            h2{
                font-size: 24px;
                font-weight: 700;
                color: #676767;
                margin-bottom: 15px;
            }
            p{
                font-size: 14px;
                line-height: 1.5;
                font-weight: 300;
                color: #676767;
            }
        }
    }
    // .product-inner::before,
    // .product-inner::after{
    //     content: ' ';
    //     position: absolute;
    //     width: 20px;
    //     height: 3px;
    //     background-color: red;
    //     transform:scaleX(0) ;
    //     transform-origin: right;
    //     transition: transform 0.5%;
    // }
    // .product-inner::before{
    //     left: 0;
    //     top: -5px;
    // }



    // .product-inner::after{
    //     right: 0;
    //     bottom: -5px;
    // }





    .product-inner.red{
        background-image: linear-gradient(to bottom right, rgb(233, 93, 93), rgb(163, 4, 4));
        &:before,
        &:after {
            content: '';
            position: absolute;
            width: 0;
            height: 4px;
            background-image: linear-gradient(to bottom right, rgb(233, 93, 93), rgb(163, 4, 4));
            transition: .3s all ease-in-out;
        }
        &:before {
            left: 0;
            top: -5px;

        }
        &:after {
            right: 0;
            bottom: -5px;
        }
        &:hover:before,
        &:hover:after {
            width: 100%;
        }
    }
    .product-inner.blue{
        background-image: linear-gradient(to bottom left, rgb(1, 91, 126),rgb(0, 217, 255));
        &:before,
        &:after {
            content: '';
            position: absolute;
            width: 0;
            height: 4px;
            background-image: linear-gradient(to bottom left, rgb(1, 91, 126),rgb(0, 217, 255));
            transition: .3s all ease-in-out;
        }
        &:before {
            left: 0;
            top: -5px;
        }
        &:after {
            right: 0;
            bottom: -5px;
        }
        &:hover:before,
        &:hover:after {
            width: 100%;
        }
    }
    .product-inner.gray{
        background-image: linear-gradient(to bottom right, rgb(229, 160, 250), rgb(96, 4, 114));
        &:before,
        &:after {
            content: '';
            position: absolute;
            width: 0;
            height: 4px;
            background-image: linear-gradient(to bottom right, rgb(229, 160, 250), rgb(96, 4, 114));
            transition: .3s all ease-in-out;
        }
        &:before {
            left: 0;
            top: -5px;
        }
        &:after {
            right: 0;
            bottom: -5px;
        }
        &:hover:before,
        &:hover:after {
            width: 100%;
        }
    }
}

</style>