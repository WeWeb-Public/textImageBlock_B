<template>
    <div class="textimageblock_B side-padding">
        <!-- wwManager:start -->
        <wwSectionEditMenu v-bind:sectionCtrl="sectionCtrl"></wwSectionEditMenu>
        <!-- wwManager:end -->
    
        <wwObject v-bind:ww-object="section.data.background" class="background" ww-category="background"></wwObject>

        <div class="container section-padding">
            <div class="row">
                <div class="titles">
                    <h1 class="section-title"><wwObject v-bind:ww-object="section.data.title"></wwObject></h1>
                    <h2 class="section-subtitle"><wwObject v-bind:ww-object="section.data.subtitle"></wwObject></h2>
                </div>
            </div>

            <div class="row margint20">
                
                <div class="blocks" v-for="(block, index) in section.data.blocks" :key="block.uniqueId">
                    <wwObject class="block-img-container" v-bind:ww-object="block.img"></wwObject>
                    <wwObject class="block-title" v-bind:ww-object="block.title"></wwObject>
                    <wwObject class="block-text" v-bind:ww-object="block.text"></wwObject>
                    <wwObject class="block-text" v-bind:ww-object="block.text2"></wwObject>
                    <div class="button-container">
                        <wwObject class="button-wrapper" v-bind:ww-object="block.button"></wwObject>
                    </div>

                    <!-- wwManager:start -->
                    <div class="edit-button-top-left" @click="removeBlock(index)">
                        <i class="wwi wwi-delete" aria-hidden="true"></i>
                    </div>
                    <!-- wwManager:end -->

                </div>

                <!-- wwManager:start -->
                <div class="blocks add-block">
                    <div class="plus" @click="addBlock()">
                        <i class="wwi wwi-add" aria-hidden="true"></i>
                    </div>
                </div>
                <!-- wwManager:end -->

            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TextAndImageBlock_B",
    props: {
        sectionCtrl: Object
    },
    data() {
        return {}
    },
    computed: {
        section() {
            return this.sectionCtrl.get();
        }
    },
    created() {
        //Initialize section data
        this.initData()
    },
    methods: {
        getNewBlock() {
            const data = {}

            data.img = wwLib.wwObject.getDefault({ type: 'ww-image' });
            data.text = wwLib.wwObject.getDefault({ type: 'ww-text', data: { text: 'Start editing by hitting the pen!' } });
            data.text2 = wwLib.wwObject.getDefault({ type: 'ww-text', data: { text: '' } });
            data.title = wwLib.wwObject.getDefault({ type: 'ww-text', data: { text: 'Rows of three images (or less) to illustrate your story.' } });
            data.button = wwLib.wwObject.getDefault({ type: 'ww-button', data: { color: 'black', borderColor: 'black' } });
    
            return data;
        },
        initData() {
            this.section.data = this.section.data || {"isNew":false,"title":{"data":{"popup":null},"font":"","link":"","size":"text-big","text":{"fr_FR":"This is the Triple Section"},"type":"text","zoom":-1,"align":"","class":["ww-anim-fade"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.21146643111968833},"blocks":[{"img":{"data":{"popup":null},"font":"","link":null,"size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":["ww-anim-grow"],"image":"https://wewebprod.s3-eu-west-1.amazonaws.com/public/images/urban/GirlBridge.jpg","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.3279281607910942},"text":{"data":{"popup":null},"font":"sans-serif","link":"","size":"text-xsmall","text":{"fr_FR":"Start editing by hitting the pen!"},"type":"text","zoom":-1,"align":"center","class":["ww-anim-fade","ww-animspeed-slow"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.36958215402524},"text2":{"data":{"popup":null},"font":"","link":"","size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":[],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.6075502245627609},"title":{"data":{"popup":null},"font":"sans-serif","link":"","size":"text-xsmall","text":{"fr_FR":"Rows of three images (or less) to illustrate your story."},"type":"text","zoom":-1,"align":"center","class":["ww-anim-fade","ww-animspeed-slow"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.6546189619287959},"button":{"data":{"popup":null},"font":"","link":"http://getweweb.com","size":"","text":{"fr_FR":"Call to action"},"type":"text","zoom":-1,"align":"","class":["ww-class-font-size-xsmall","ww-class-btn-border-small","ww-class-btn-shadow-bottom-small","ww-class-btn-padding-small","ww-class-btn-format-round-small","ww-anim-fade"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"#000000","backgroundColor":"#FFFFFF"},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.7361627781705045},"textImg":"Coucou !","uniqueId":2,"titleStyle":{"size":"text-small"}},{"img":{"data":{"popup":null},"font":"","link":null,"size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":["ww-anim-grow"],"image":"https://wewebprod.s3-eu-west-1.amazonaws.com/designs/46/sections/70Qry53tJrWrtS2zCrkuDME2XJgBjb66.jpg","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.2108381846122258},"text":{"data":{"popup":null},"font":"sans-serif","link":"","size":"text-xsmall","text":{"fr_FR":"Don't forget to use the animations for a stunning effect!"},"type":"text","zoom":-1,"align":"center","class":["ww-anim-fade","ww-animspeed-slow"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.40493381725059474},"text2":{"data":{"popup":null},"font":"","link":"","size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":[],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.0595187148767411},"title":{"data":{"popup":null},"font":"sans-serif","link":"","size":"text-xsmall","text":{"fr_FR":"Click on any icon to edit specific items (change pics, effects...)"},"type":"text","zoom":-1,"align":"center","class":["ww-anim-fade","ww-animspeed-slow"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.08031675437451313},"button":{"data":{"popup":null},"font":"","link":"http://getweweb.com","size":"","text":{"fr_FR":"Call to action"},"type":"text","zoom":-1,"align":"","class":["ww-class-btn-format-round-small","ww-class-btn-padding-small","ww-class-btn-shadow-bottom-small","ww-class-btn-border-small","ww-anim-fade"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"#000000","backgroundColor":"#FFFFFF"},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.3448095386851411},"textImg":"Coucou !","uniqueId":3,"titleStyle":{"size":"text-small"}},{"img":{"data":{"popup":null},"font":"","link":"","size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":["ww-anim-grow"],"image":"https://wewebprod.s3-eu-west-1.amazonaws.com/public/images/people/ManSubway.jpg","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.41177625137169116},"text":{"data":{"popup":null},"font":"sans-serif","link":"","size":"text-xsmall","text":{"fr_FR":"You can delete the pictures by hitting the \"x\" "},"type":"text","zoom":-1,"align":"center","class":["ww-anim-fade","ww-animspeed-slow"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.6662974680760885},"text2":{"data":{"popup":null},"font":"","link":"","size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":[],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.5308053351622548},"title":{"data":{"popup":null},"font":"sans-serif","link":"","size":"text-xsmall","text":{"fr_FR":"You can add as many picture as you want by hitting the \"+\" "},"type":"text","zoom":-1,"align":"center","class":["ww-anim-fade","ww-animspeed-slow"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.7280240993200022},"button":{"data":{"popup":null},"font":"","link":"#/","size":"","text":{"fr_FR":"Call to action"},"type":"text","zoom":-1,"align":"","class":["ww-class-btn-format-round-small","ww-class-btn-border-small","ww-class-btn-shadow-bottom-small","ww-class-btn-padding-small","ww-anim-fade"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"#000000","backgroundColor":"#FFFFFF"},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.4535948637719338},"textImg":"Coucou !","uniqueId":1484325586802.2131}],"subtitle":{"data":{"popup":null},"font":"","link":"","size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":[],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.3765856590079877},"background":{"data":{"popup":null},"font":"","link":null,"size":"","text":{"fr_FR":""},"type":"text","zoom":-1,"align":"","class":[],"image":"#FFFFFF","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.9683046020751509},"titleStyle":{"size":"text-big","color":"#263238"},"sectionTitle":"Triple"}

            if (_.isEmpty(this.section.data.blocks))
                this.section.data.blocks = [this.getNewBlock(), this.getNewBlock(), this.getNewBlock()]
            
            if (!this.section.data.background)
                this.section.data.background = wwLib.wwObject.getDefault({ type: 'ww-color' });
            
            if (!this.section.data.title)
                this.section.data.title = wwLib.wwObject.getDefault({ type: 'ww-text' });
            
            if (!this.section.data.subtitle)
                this.section.data.subtitle = wwLib.wwObject.getDefault({ type: 'ww-text' });

            this.sectionCtrl.update(this.section);
        },
        addBlock(options) {
            this.section.data.blocks.push(this.getNewBlock());
            this.sectionCtrl.update(this.section);
        },
        removeBlock(index) {
            this.section.data.blocks.splice(index, 1);
            this.sectionCtrl.update(this.section);
        }
    }
};
</script>

<style scoped>
.textimageblock_B .container {
    width: 100%;
    position: relative;
}

.textimageblock_B .background {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
}

.textimageblock_B .side-padding {
    padding-left: 5px;
    padding-right: 5px;
}

.textimageblock_B .block-img-container {
    width: 100%;
    position: relative;
}

.textimageblock_B .block-img {
    width: 100%;
}

.textimageblock_B .block-title {
    margin-top: 10px;
}

.textimageblock_B .block-text {
    margin-top: 10px;
}

.textimageblock_B .button-container {
    text-align: center;
    width: 100%;
    margin-top: 20px;
    margin-bottom: 40px;
}

.textimageblock_B .section-subtitle {
    margin-top: 10px;
}

.textimageblock_B .section-padding {
    padding: 30px 15px
}

.textimageblock_B .section-padding {
    padding: 30px 15px
}

.textimageblock_B .margint20 {
    margin-top: 20px;
}

.textimageblock_B .row {
    display: -ms-flexbox;
    display: flex;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    margin-right: -15px;
    margin-left: -15px;
}

.textimageblock_B .plus {
  color: white;
  cursor: pointer;
  pointer-events: all;
  font-size: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 100%;
  background-color: #1763A9;
  background: linear-gradient(to right, #1763A9 0%, #2E85C2 100%);
}

.textimageblock_B .add-block {
    display: flex;
    justify-content: center;
}

.textimageblock_B .edit-button-top-left {
    position: absolute;
    left: -2px;
    top: -17px;
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 100%;
    text-align: center;
    font-size: 18px;
    line-height: 36px;
    cursor: pointer;
    pointer-events: all;
    z-index: 3;
    color: white;
    background-color: #E73055;
    background: linear-gradient(to right, #E73055 0%, rgb(175, 33, 61) 100%);
}

.textimageblock_B .titles {
    position: relative;
    width: 100%;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    -ms-flex: 0 0 100%;
    flex: 0 0 100%;
    max-width: 100%;
}

.textimageblock_B .blocks {
    position: relative;
    width: 100%;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    -ms-flex: 0 0 100%;
    flex: 0 0 100%;
    max-width: 100%;
    margin-bottom: 20px;
}

@media (min-width: 768px) {
    .textimageblock_B .side-padding {
        padding-left: 5%;
        padding-right: 5%;
    }
    .textimageblock_B .section-padding {
        padding: 50px 30px
    }
    .textimageblock_B .button-container {
        margin-bottom: 20px;
    }
}

@media (min-width: 992px) {
    .textimageblock_B .section-padding {
        padding: 75px 50px
    }
    .textimageblock_B .blocks {
        -ms-flex: 0 0 33.333333%;
        flex: 0 0 33.333333%;
        max-width: 33.333333%;
    }
}

@media (min-width: 1200px) {}
</style>
