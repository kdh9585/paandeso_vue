<template>
    <!-- modal window -->
    <div class="modal-wrap">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title">
                            <slot name="title"></slot>
                        </h5> 
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="onClose">
                        <span aria-hidden="true">&times;</span>
                    </button>
                    </div>
                    <div class="modal-body">
                        <p><slot name="body"></slot></p>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-danger" @click="onDelete">확인</button>
                        <button type="button" class="btn btn-secondary" @click="onClose">취소</button>
                    </div>
                </div>
            </div>
    </div>
</template>

<script>
    import { getCurrentInstance } from 'vue';
    export default {
        emits: ['close','delete'],
        setup(){
            const {emit} = getCurrentInstance();

            const onClose = () =>{
                emit('close');
            }
            const onDelete = ()=>{
                emit('delete');
            }
            return{
                onClose,
                onDelete
            }
        }

    }
</script>

<style>
    .modal-wrap {
        position: fixed;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 9;
    }
</style>