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
        <tr v-for="(item, index) in datas" :key="item.no_rawat">
          <td>{{ index + 1 }}</td>
          <td>{{ item.no_rawat }}</td>
          <td>{{ item.stts_daftar }}</td>
          <td>{{ item.nm_dokter }}</td>
          <td>{{ item.no_rkm_medis }}</td>
          <td>{{ item.nm_pasien }}</td>
          <td>{{ item.nm_poli }}</td>
          <td>{{ item.kd_pj }}</td>
          <td>
            <div>
              <span
                :style="{ color: getStatusColor(item.status_task3) }"
                @click.prevent.self="openModal(item.task3, 'task3')"
              >
                Task 3: {{ item.task3 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(item.status_task4) }"
                @click.prevent.self="openModal(item.task4, 'task4')"
              >
                Task 4: {{ item.task4 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(item.status_task5) }"
                @click.prevent.self="openModal(item.task5, 'task5')"
              >
                Task 5: {{ item.task5 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(item.status_task6) }"
                @click.prevent.self="openModal(item.task6, 'task6')"
              >
                Task 6: {{ item.task6 || "N/A" }} </span
              ><br />
              <span
                :style="{ color: getStatusColor(item.status_task7) }"
                @click.prevent.self="openModal(item.task7, 'task7')"
              >
                Task 7: {{ item.task7 || "N/A" }}
              </span>
            </div>
          </td>
          <td>
            <button @click="kirimBerkas(item.no_rawat)">Kirim</button>
          </td>
        </tr>
      </tbody>
    </table>

    <TimeModal
      :visible="modalVisible"
      :currentValue="currentTaskValue"
      :taskName="currentTaskName"
      @close="closeModal"
    />
  </div>
</template>

<script>
import TimeModal from "../../components/TimeModal.vue"

export default {
  components: {
    TimeModal,
  },
  data() {
    return {
      datas: [
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
      ],
      modalVisible: false,
      currentTaskValue: "",
      currentTaskName: "",
    }
  },
  methods: {
    kirimBerkas(no_rawat) {
      alert(`Kirim berkas: ${no_rawat}`)
    },
    openModal(taskValue, taskName) {
      this.currentTaskValue = taskValue
      this.currentTaskName = taskName
      this.modalVisible = true
    },
    closeModal() {
      this.modalVisible = false
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
