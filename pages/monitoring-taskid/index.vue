<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>No</th>
          <th>No Rawat</th>
          <th>Stts Daftar</th>
          <th>Nama Dokter</th>
          <th>NoMR</th>
          <th>Nama Pasien</th>
          <th>Nama Poli</th>
          <th>Penjamin</th>
          <th>Informasi</th>
          <th>ACTION</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(registration, index) in registrations"
          :key="registration.no_rawat"
        >
          <td>{{ index + 1 }}</td>
          <td>{{ registration.no_rawat }}</td>
          <td>{{ registration.stts_daftar }}</td>
          <td>{{ registration.nm_dokter }}</td>
          <td>{{ registration.no_rkm_medis }}</td>
          <td>{{ registration.nm_pasien }}</td>
          <td>{{ registration.nm_poli }}</td>
          <td>{{ registration.kd_pj }}</td>
          <td>
            <div>
              <span
                :style="{ color: getStatusColor(registration.status_task3) }"
              >
                Task 3: {{ registration.task3 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(registration.status_task4) }"
              >
                Task 4: {{ registration.task4 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(registration.status_task5) }"
              >
                Task 5: {{ registration.task5 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(registration.status_task6) }"
              >
                Task 6: {{ registration.task6 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(registration.status_task7) }"
              >
                Task 7: {{ registration.task7 || "N/A" }}
              </span>
            </div>
          </td>
          <td>
            <!-- Placeholder for action buttons (e.g., Edit, Delete) -->
            <button @click="editRegistration(registration.no_rawat)">
              Edit
            </button>
            <button @click="deleteRegistration(registration.no_rawat)">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      registrations: [
        {
          no_reg: "001",
          no_rawat: "2024/08/09/000001",
          kd_pj: "BPJ",
          no_rkm_medis: "105118",
          nm_pasien: "AMALIA HIDAYATI",
          tgl_registrasi: "2024-08-09",
          kd_dokter: "DOK1363",
          nm_dokter: "dr. Athaillah A.Latif Sp.OG",
          kd_poli: "UNT02",
          nm_poli: "Poli Obgyn",
          stts_daftar: "Lama",
          no_rujukan: null,
          nobooking: "20240809000001",
          resep: null,
          task3: null,
          status_task3: "grey",
          task4: null,
          status_task4: "grey",
          task5: null,
          status_task5: "grey",
          task6: null,
          status_task6: "grey",
          task7: null,
          status_task7: "grey",
        },
        {
          no_reg: "006",
          no_rawat: "2024/08/08/000006",
          kd_pj: "BPJ",
          no_rkm_medis: "104434",
          nm_pasien: "SAERAH M BASYAH",
          tgl_registrasi: "2024-08-08",
          kd_dokter: "DOK1365",
          nm_dokter: "dr. Heriadi F, SpPD, K-KV, FINASIM",
          kd_poli: "UNT05",
          nm_poli: "Poli Penyakit Dalam",
          stts_daftar: "Lama",
          no_rujukan: "001200030724P000883",
          nobooking: "20240808000006",
          resep: "2024-08-08 15:51:02",
          task3: "2024-08-08 15:30:32",
          status_task3: "green",
          task4: "2024-08-08 15:42:32",
          status_task4: "green",
          task5: "2024-08-08 15:52:06",
          status_task5: "green",
          task6: "2024-08-08 16:24:47",
          status_task6: "green",
          task7: "2024-08-08 16:40:47",
          status_task7: "green",
        },

        // ... (other objects from your JSON data)
      ],
    }
  },
  methods: {
    editRegistration(no_rawat) {
      alert(`Editing registration: ${no_rawat}`)
    },
    deleteRegistration(no_rawat) {
      alert(`Deleting registration: ${no_rawat}`)
    },
    getStatusColor(status) {
      switch (status) {
        case "green":
          return "green"
        case "yellow":
          return "yellow"
        case "red":
          return "red"
        case "grey":
          return "grey"
        default:
          return "black"
      }
    },
  },
}
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
}

thead {
  background-color: #f2f2f2;
}

th,
td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #4caf50;
  color: white;
}

tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

tbody tr:hover {
  background-color: #ddd;
}

button {
  margin-right: 5px;
  padding: 5px 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
