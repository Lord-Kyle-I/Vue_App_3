<script>
import PersonTable from "@/components/PersonTable.vue";
import ShortDate from "@/models/ShortDate.js";

export default {
  name: 'App',

  components: {
    PersonTable
  },

  // data: all the data for the app
  data: function () {
    return {

      relationship: {
        name: '',
        relation: '',
        link: null,
      },

      tooltips: [],

      people: [
        {
          isFavorite: false,
          isAlive: false,
          country: 'Germany',
          name: 'Albert Einstein',
          dateOfBirth: new ShortDate('03', "14", "1879"),
          placeOfBirth: 'Ulm, Württemberg, Germany',
          dateOfDeath: new ShortDate("04", "18", "1955"),
          placeOfDeath: 'Princeton, New Jersey, USA',
          placeOfBurial: 'Cremated; ashes scattered (undisclosed location, reportedly Delaware River area)',
          relationships: [],
          defaultPlace: 'Princeton, New Jersey, USA',
        },
        {
          isAlive: false,
          country: 'United States',
          name: 'Abraham Lincoln',
          dateOfBirth: new ShortDate(0o2, 12, 1809),
          placeOfBirth: 'Near Hodgenville, Kentucky, USA',
          dateOfDeath: new ShortDate(0o4, 15, 1865),
          placeOfDeath: 'Washington, D.C., USA',
          placeOfBurial: 'Oak Ridge Cemetery, Springfield, Illinois, USA',
          relationships: [],
          defaultPlace: 'Springfield, Illinois, USA',
        },
        {
          isAlive: false,
          country: 'Poland / France',
          name: 'Marie Curie',
          dateOfBirth: new ShortDate(11, 7, 1867),
          placeOfBirth: 'Warsaw, Congress Poland (Russian Empire)',
          dateOfDeath: new ShortDate(7, 4, 1934),
          placeOfDeath: 'Passy (near Sallanches), Haute-Savoie, France',
          placeOfBurial: 'Panthéon, Paris, France',
          relationships: [],
          defaultPlace: 'Paris, France',
        },
        {
          isAlive: false,
          country: 'Italy',
          name: 'Leonardo da Vinci',
          dateOfBirth: new ShortDate(4, 15, 1452),
          placeOfBirth: 'Anchiano (near Vinci), Republic of Florence, Italy',
          dateOfDeath: new ShortDate(5, 2, 1519),
          placeOfDeath: 'Clos-Lucé, Amboise, France',
          placeOfBurial: 'Chapel of Saint-Hubert, Château d\'Amboise, France',
          relationships: [],
          defaultPlace: 'Florence / Vinci, Italy',
        },
      ]
    };
  },

  // methods: usually "events" triggered by v-on:
  methods: {

    //add and edit function
    addPerson: function (person) {
      this.people.push(person)
    },

    deletePerson: function (person) {
      console.log('im here')
      const indexToRemove = this.people.indexOf(person);
      this.people.splice(indexToRemove, 1)
    },

    clearForm() {
      setTimeout(() => {
        //clear form logic
      }, 100)
    }
  },

  // computed: values that are updated and cached if dependencies change
  computed: {


    relationships() {
      return this.person.relationships
    }
  },

  //mounted:  called after the instance has been mounted,
  mounted: function () {

  },

  // watch:   calls the function if the value changes
  // https://travishorn.com/add-localstorage-to-your-vue-app-in-2-lines-of-code-56eb2c9f371b
  watch: {


  },
}
</script>

<template>
  <div>
    <header>
      <nav class="navbar bg-body-tertiary">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">
            <div class="d-flex gap-1"><span class="fs-3 text-brand libre-baskerville-brand">Family Chart
                          </span>
              <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor"
                   class="bi bi-leaf-fill text-brand align-self-center" viewBox="0 0 16 16">
                <path
                    d="M1.4 1.7c.217.289.65.84 1.725 1.274 1.093.44 2.885.774 5.834.528 2.02-.168 3.431.51 4.326 1.556C14.161 6.082 14.5 7.41 14.5 8.5q0 .344-.027.734C13.387 8.252 11.877 7.76 10.39 7.5c-2.016-.288-4.188-.445-5.59-2.045-.142-.162-.402-.102-.379.112.108.985 1.104 1.82 1.844 2.308 2.37 1.566 5.772-.118 7.6 3.071.505.8 1.374 2.7 1.75 4.292.07.298-.066.611-.354.715a.7.7 0 0 1-.161.042 1 1 0 0 1-1.08-.794c-.13-.97-.396-1.913-.868-2.77C12.173 13.386 10.565 14 8 14c-1.854 0-3.32-.544-4.45-1.435-1.124-.887-1.889-2.095-2.39-3.383-1-2.562-1-5.536-.65-7.28L.73.806z"/>
              </svg>
            </div>
          </a>
        </div>
      </nav>
      <div>
        <img src="@/images/pexels-cottonbro-8848776.jpg" class="w-100 object-fit-cover"
             alt="Three sitting people looking at old photos">
      </div>
    </header>
    <div class="containter-fluid">
      <main>
        <div class="container mt-5 mb-3 p-3 bg-light shadow d-flex flex-column gap-3">
          <h2 class="fw-semibold">Welcome to Family Chart!</h2>
          <p>
            Family Chart is your intuitive portal for organizing, preserving, and linking your lineage across
            generations. Designed to streamline your genealogy research, FamilyChart lets you easily build
            detailed
            individual profiles, edit vital details, and filter through living and deceased family members by
            location. Whether you are adding new relatives or mapping out complex connections, FamilyChart
            brings
            your family history together in one clear, searchable workspace.
          </p>
        </div>
        <div class="pt-2 pb-2 mt-5 mb-5 main-content container-lg bg-accent">
          <person-table :people="people" @add-person="addPerson" @delete-person="deletePerson"></person-table>
        </div>
      </main>
      <footer class="bg-brand text-light">
        &copyKyle Leverence 2027
      </footer>
    </div>
  </div>

</template>

<style scoped>

</style>
