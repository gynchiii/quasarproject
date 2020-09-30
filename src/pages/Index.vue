<template>
  <q-page class="flex flex-center">
      <div class="q-pa-sm">
    <div class="q-gutter-sm row items-start">
      <q-select
        filled
        v-model="single"
        label="Data Inicial"
        style="width: 120px"
      />

    <q-select
        filled
        v-model="single"
        label="Data Final"
        style="width: 120px"
      />
       <q-select
        filled
        v-model="single"
        :options="options"
        label="Todas"
        style="width: 120px"
      />
       <q-select
        filled
        v-model="single"
        label="Todos"
        style="width: 120px"
      />
      <q-btn class="q-pa-sm" style="background:#4527a0" icon="filter_alt" label="Filtrar" text-color="white" />
    </div>
  </div>
  <div class="q-pa-md">
    <div class="q-gutter-y-md" style="width: 900px">
      <q-card>
        <q-tabs
          v-model="tab"
          dense
          class="text-grey"
          active-color="primary"
          indicator-color="primary"
          align="justify"
          narrow-indicator
        >
          <q-tab name="general" label="Geral" />
          <q-tab name="corrections" label="Correções" />
          <q-tab name="relat" label="Relatórios" />
        </q-tabs>

        <q-separator />

        <q-tab-panels v-model="tab" animated>
          <q-tab-panel name="general">
           <q-table
        class="my-sticky-header-table"
        :data="data"
        :columns="columns"
        row-key="name"
        flat
        bordered
    />
          </q-tab-panel>
          <q-tab-panel name="corrections">
           <q-table
        class="my-sticky-header-table"
        :data="data"
        :columns="columns"
        row-key="name"
        flat
        bordered
    />
          </q-tab-panel>
          <q-tab-panel name="relat">
    <q-table
      :data="data"
      :columns="columns"
      row-key="name"
      hide-bottom
    />
          </q-tab-panel>
        </q-tab-panels>
        <q-btn></q-btn>
      </q-card>
    </div>
  </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      tab: 'general',
      single: null,

      options: [
        'Academia', 'Contrução', 'Direito'
      ],
      columns: [
        {
          name: 'name',
          required: true,
          label: 'Usuário',
          align: 'left',
          field: row => row.name,
          format: val => `${val}`,
          sortable: true
        },
        {
          name: 'area',
          required: true,
          label: 'Área',
          align: 'center',
          field: row => row.area,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'cpost', label: 'Posts Criados', field: 'cposts', sortable: true },
        { name: 'postc', label: 'Posts Corrigidos', field: 'postsc', sortable: true }
      ],

      data: [
        {
          name: 'Matheus',
          area: 'Matemática',
          cposts: 6.0,
          postsc: 24
        },
        {
          name: 'Matheus',
          area: 'Filosofia',
          cposts: 9.0,
          postsc: 37
        },
        {
          name: 'Matheus',
          area: 'Matemática',
          cposts: 16.0,
          postsc: 23
        },
        {
          name: 'Matheus',
          area: 'Ciências',
          cposts: 3.7,
          postsc: 67
        },
        {
          name: 'Matheus',
          area: 'História',
          cposts: 16.0,
          postsc: 49
        }
      ]
    }
  }
}
</script>
<style scoped>
  :root{
  font-family: Roboto;
  font-style: normal;
  font-weight: 300;
  font-size: 16px;
  line-height: 24px;
  }
</style>
