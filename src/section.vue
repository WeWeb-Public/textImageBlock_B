<template>
    <div class="textimageblock_B side-padding">
        <!-- wwManager:start -->
        <wwSectionEditMenu v-bind:sectionCtrl="sectionCtrl"></wwSectionEditMenu>
        <!-- wwManager:end -->
        <wwObject v-bind:ww-object="section.data.background" class="background" ww-category="background"></wwObject>
        <div class="container section-padding">
            <div class="row">
                <div class="titles">
                    <h1 class="section-title">
                        <wwObject v-bind:ww-object="section.data.title"></wwObject>
                    </h1>
                    <h2 class="section-subtitle">
                        <wwObject v-bind:ww-object="section.data.subtitle"></wwObject>
                    </h2>
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
                    <div v-show="editMode" class="edit-button-top-left" @click="removeBlock(index)">
                        <i class="wwi wwi-delete" aria-hidden="true"></i>
                    </div>
                    <!-- wwManager:end -->
                </div>
                <!-- wwManager:start -->
                <div v-show="editMode" class="blocks add-block">
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
    name: "__COMPONENT_NAME__",
    props: {
        sectionCtrl: Object
    },
    data() {
        return {}
    },
    computed: {
        section() {
            return this.sectionCtrl.get();
        },
        // wwManager:start
        editMode() {
            return this.sectionCtrl.getEditMode() == 'CONTENT'
        }
        // wwManager:end
    },
    created() {
        this.initData()
    },
    methods: {
        getNewBlock() {
            const data = {
                 img: wwLib.wwObject.getDefault({ type: 'ww-image' }),
                text: wwLib.wwObject.getDefault({ type: 'ww-text' }),
                text2: wwLib.wwObject.getDefault({ type: 'ww-text' }),
                title: wwLib.wwObject.getDefault({ type: 'ww-text' }),
                button: wwLib.wwObject.getDefault({ type: 'ww-button', data: { color: 'black', borderColor: 'black' } })
            }
            return data;
        },
        initData() {
            this.section.data = this.section.data || {}

            if (_.isEmpty(this.section.data.blocks)) {
                this.section.data.blocks = [this.getNewBlock(), this.getNewBlock(), this.getNewBlock()]
            }
            if (!this.section.data.background) {
                this.section.data.background = wwLib.wwObject.getDefault({ type: 'ww-color' });
            }
            if (!this.section.data.title) {
                this.section.data.title = wwLib.wwObject.getDefault({ type: 'ww-text' });
            }
            if (!this.section.data.subtitle) {
                this.section.data.subtitle = wwLib.wwObject.getDefault({ type: 'ww-text' });
            }
            this.sectionCtrl.update(this.section);
        },
        // wwManager:start
        addBlock(options) {
            this.section.data.blocks.push(this.getNewBlock());
            this.sectionCtrl.update(this.section);
        },
        removeBlock(index) {
            this.section.data.blocks.splice(index, 1);
            this.sectionCtrl.update(this.section);
        }
        // wwManager:end
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
