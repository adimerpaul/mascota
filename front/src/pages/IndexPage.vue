<template>
  <div class="q-pa-md">
    <q-stepper
      v-model="step"
      header-nav
      ref="stepper"
      color="primary"
      animated
    >
      <q-step
        :name="1"
        title="1.- Datos propietario"
        icon="settings"
        :done="step > 1"
      >
        <q-card>
          <q-card-section class="bg-primary text-white q-pa-xs">
            <div class="text-subtitle2">Datos del Responsable</div>
          </q-card-section>
          <q-separator />
          <q-card-section>
            <div class="row">
              <q-select class="col-12 col-md-3" dense v-model="dato.tipoDoc" outlined :rules="[ val => val.length > 0 || 'Tipo Doc es requerido' ]" label="Tipo Doc." :options="['CI - CEDULA DE IDENTIDAD', 'CEX - CEDULA DE IDENTIDAD DE EXTRANJERO', 'PAS - PASAPORTE', 'OD - OTRO DOCUMENTO DE IDENTIDAD', 'NIT - NÚMERO DE IDENTIFICACIÓN TRIBUTARIA']"/>
              <q-input class="col-12 col-md-3" dense v-model="dato.docNumero" label="Doc. Numero" outlined lazy-rules :rules="[ val => val.length > 0 || 'Doc numero es requerido' ]"/>
              <q-input class="col-12 col-md-3" dense v-model="dato.apellidos" label="Apellidos" outlined lazy-rules :rules="[ val => val.length > 0 || 'Apellido es requerido' ]"/>
              <q-input class="col-12 col-md-3" dense v-model="dato.nombres" label="Nombres" outlined lazy-rules :rules="[ val => val.length > 0 || 'Nombre es requerido' ]"/>
            </div>
          </q-card-section>
        </q-card>
        <q-card>
          <q-card-section class="bg-primary text-white q-pa-xs">
            <div class="text-subtitle2">Domicilio</div>
          </q-card-section>
          <q-separator />
          <q-card-section>
            <div class="row">
              <q-input class="col-12 col-md-3" dense v-model="dato.calle" label="Calle" outlined lazy-rules hint=""/>
              <q-input class="col-12 col-md-3" dense v-model="dato.numero" label="Numero" outlined lazy-rules hint=""/>
              <q-input class="col-12 col-md-3" dense v-model="dato.piso" label="Piso" outlined lazy-rules hint=""/>
              <q-input class="col-12 col-md-3" dense v-model="dato.depto" label="Departamento" outlined lazy-rules hint=""/>
            </div>
          </q-card-section>
        </q-card>
        <q-card>
          <q-card-section class="bg-primary text-white q-pa-xs">
            <div class="text-subtitle2">Localidad</div>
          </q-card-section>
          <q-separator />
          <q-card-section>
            <div class="row">
            <div class="col-12 col-md-6">
              <span class="text-bold">El Domicilio es Extranjero ?</span>
              <q-option-group
                inline
                v-model="group"
                :options="options"
                color="primary"
              />
            </div>
            <q-select :options="['Oruro']" class="col-12 col-md-6" dense v-model="dato.localidad" label="Localidad" outlined lazy-rules hint=""/>
            </div>
          </q-card-section>
        </q-card>
        <q-card>
          <q-card-section class="bg-primary text-white q-pa-xs">
            <div class="text-subtitle2">Contacto</div>
          </q-card-section>
          <q-separator />
          <q-card-section>
            <div class="row">
              <q-input class="col-12 col-md-6" dense v-model="dato.telefono" label="Num. Telefono" outlined lazy-rules hint=""/>
              <q-input class="col-12 col-md-6" dense v-model="dato.correo" label="Correo electronico" type="email" outlined lazy-rules hint=""/>
            </div>
          </q-card-section>
        </q-card>
        <q-stepper-navigation>
          <q-btn @click="step = 2" icon="keyboard_tab" color="green" label="Seleccionar/Cargar Mascota" />
        </q-stepper-navigation>
      </q-step>
<!--      caption="Optional"-->
      <q-step
        :name="2"
        title="2.- Seleccionar/Cargar Mascota"
        icon="create_new_folder"
        :done="step > 2"
      >
        An ad group contains one or more ads which target a shared set of keywords.

        <q-stepper-navigation>
          <q-btn @click="step = 4" color="primary" label="Continue" />
          <q-btn flat @click="step = 1" color="primary" label="Back" class="q-ml-sm" />
        </q-stepper-navigation>
      </q-step>

      <q-step
        :name="3"
        title="Ad template"
        icon="assignment"
        disable
      >
        This step won't show up because it is disabled.
      </q-step>

      <q-step
        :name="4"
        title="Create an ad"
        icon="add_comment"
      >
        Try out different ad text to see what brings in the most customers, and learn how to
        enhance your ads using features like ad extensions. If you run into any problems with
        your ads, find out how to tell if they're running and how to resolve approval issues.

        <q-stepper-navigation>
          <q-btn color="primary" label="Finish" />
          <q-btn flat @click="step = 2" color="primary" label="Back" class="q-ml-sm" />
        </q-stepper-navigation>
      </q-step>
    </q-stepper>
  </div>
</template>

<script>

export default {
  data () {
    return {
      group: 'NO',
      options: [
        {
          label: 'NO',
          value: 'NO'
        },
        {
          label: 'SI',
          value: 'SI'
        },
      ],
      dato:{},
      step: 2
    }
  }
}
</script>
