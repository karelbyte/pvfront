<template>
  <q-list bordered separator>
      <span v-for="item in list" :key="item.id">
      <q-item   
        clickable v-ripple
        :active="active == item.id"
        active-class="bg-green-2 text-grey-8"
        @click="select(item)"
        v-if="item.type == 'single'"
      >
        <q-item-section avatar>
         <q-icon color="blue-grey-7" :name="item.icon" />
        </q-item-section>
        <q-item-section color="blue-grey-7">{{item.description}}</q-item-section>
      </q-item>
       <q-expansion-item v-else
        expand-separator
        :icon="item.icon"
        :label="item.description"
        >
        <q-card>
          <q-card-section>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius reprehenderit eos corrupti
            commodi magni quaerat ex numquam, dolorum officiis modi facere maiores architecto suscipit iste
            eveniet doloribus ullam aliquid.
          </q-card-section>
        </q-card>
      </q-expansion-item>
      <q-separator />
     </span>
    </q-list>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'Menu',
  setup() {

    const list = [
       {id: 1, type: 'single', owner: 0, description: 'Control Diario', icon: 'fa fa-th-large', patch: ''},
       {id: 2, type: 'single', owner: 0, description: 'Prospectos', icon: 'fa fa-th-large', patch: ''},
       {id: 3, type: 'single', owner: 0, description: 'Clientes', icon: 'fa fa-th-large', patch: ''},
       {id: 4, type: 'single', owner: 0, description: 'Instalaciones', icon: 'fa fa-th-large', patch: ''},
       {id: 5, type: 'single', owner: 0, description: 'Mantenimientos', icon: 'fa fa-th-large', patch: ''},
       {id: 6, type: 'multiple', owner: 0, description: 'Almacenes', icon: 'fa fa-th-large', patch: ''},
    ]

    let active = ref(0)

    const select = function (item) {
       this.active = item.id
    }
    
    return {
       select,
       active,
       list
   }

  },
})
</script>
