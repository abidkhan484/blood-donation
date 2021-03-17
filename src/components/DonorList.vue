<template>
  <table class="table table-striped table-responsive">
    <thead>
      <tr>
        <th>Name</th>
        <th>Blood Group</th>
        <th>Contact Number</th>
        <th>Last Donation Date</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="donor in getAllDonors" :key="donor.sl">
        <td>{{ donor.name }}</td>
        <td>{{ donor.bloodGroup }}</td>
        <td>{{ donor.phone }}</td>
        <td>{{ donor.lastDonation }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
const google_sheet_url =
  "https://spreadsheets.google.com/feeds/list/1wmPGMpRWQel_1qj-3MpOoUkUEHf7u4ktA8Wsei7xT44/1/public/values?alt=json";

export default {
  name: "DonorList",
  created() {
    fetch(google_sheet_url)
      .then((resp) => resp.json())
      .then((donors_json) => {
        this.donors = donors_json.feed.entry.map((donor) => {
          return {
            sl: donor.sl,
            name: donor.gsx$name.$t,
            bloodGroup: donor.gsx$bloodgroup.$t,
            phone: donor.gsx$contactnumber.$t,
            lastDonation: donor.gsx$lastblooddonationdateapprox.$t.split("\n").join(", "),
          };
        });
      });
  },
  data() {
    return { donors: [] };
  },
  computed: {
    getAllDonors() {
      return this.donors;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
