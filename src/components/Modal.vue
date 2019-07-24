<template>
  <div>
    <div v-if="showModal">
     <transition name="modal">
      <div class="modal-mask">
        <div class="modal-wrapper">
           <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title namerest" >{{ titleRestuarant }}</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true" @click="onClickCloseModal()">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                  <p class= textsize>Taste Rate :</p>
                    <star-rating v-bind:increment="0.5"
                                 v-bind:max-rating="5"
                                inactive-color="grey"
                                 active-color="#FDE171"
                                 v-bind:star-size="50"
                                 v-model="starRating">
                    </star-rating><br>
                  <form action="/action_page.php" id="usrform" ><p class = textsize>Price:</p>
                      <input type="text" name="usrname">
                        <input type="submit">
                  </form><br>
                    <p class= textsize>Best Menu :</p>
                    <textarea rows="4" cols="50" name="comment" form="usrform" class = "overflow-auto"></textarea>
                    <p class= textsize>Others :</p>
                    <textarea rows="4" cols="50" name="comment" form="usrform" class = "overflow-auto"></textarea>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" @click="onClickCloseModal()">Close</button>
                    <button type="button" class="btn btn-primary">Save changes</button>
                </div>
           </div>
        </div>
        </div>
        <Model :starRating = "starRating"/>
      </div>
    </transition>
   </div>
  </div>
</template>
<script>
import StarRating from 'vue-star-rating'
export default {
  props: ['showModal', 'onClickCloseModal' , 'titleRestuarant'],
  components: {
  StarRating
},
data() {
  return{
    starRating: '',
  }
},
methods: {

}

}
</script>
<style scoped>
    .modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

    .modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

    .textsize {
  font-size: 20px;
  }

    .namerest {
  font-size: 30px;
  margin-left: auto;


  }
  .modal-body{
    color: black;
  }

  .modal-title {
    color: black;
  }


</style>

