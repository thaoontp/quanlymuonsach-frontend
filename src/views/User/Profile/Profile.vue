<template>
  <div class="containPage">
    <div class="contentPage">
      <section class="">
        <div class="">
          <div class="row d-flex justify-content-center align-items-center">
            <div class="col">
              <div class="card">
                <!-- Thẻ card header -->
                <div class="card-header">
                  <div class="d-flex justify-content-center text-center py-1">
                    Độc giả
                  </div>
                </div>
                <!-- Thẻ card body -->
                <div class="card-body">
                  <div class="row">
                    <!-- Avatar bên phải -->

                    <!-- Thông tin bên trái -->
                    <div class="col-sm-9">
                      <div class="mb-5">
                        <!-- <p class="lead fw-normal mb-1">Thông tin cá nhân</p> -->
                        <div class="" style="background-color: #f8f9fa">
                          <div class="card-body">
                            <div class="row">
                              <div class="col-sm-3">
                                <p class="mb-0">Họ tên</p>
                              </div>
                              <div class="col-sm-9">
                                <p class="text-muted mb-0">{{ data.Ten }}</p>
                              </div>
                            </div>
                            <hr />
                            <div class="row">
                              <div class="col-sm-3">
                                <p class="mb-0">Số điện thoại</p>
                              </div>
                              <div class="col-sm-9">
                                <p class="text-muted mb-0">
                                  {{ data.DienThoai }}
                                </p>
                              </div>
                            </div>
                            <hr />
                            <div class="row">
                              <div class="col-sm-3">
                                <p class="mb-0">Địa chỉ</p>
                              </div>
                              <div class="col-sm-9">
                                <p class="text-muted mb-0">{{ data.DiaChi }}</p>
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>

                    <div
                      class="col-sm-3 d-flex justify-content-center align-items-center"
                    >
                      <div>
                        <img
                          v-if="data.Avatar != undefined"
                          :src="'http://localhost:3000/' + data.Avatar"
                          alt="Generic placeholder image"
                          class="img-fluid"
                          style="width: 125px; z-index: 1"
                        />
                        <div class="my-3">
                          <!-- Thêm dòng trống phía dưới ảnh -->
                          <router-link to="/editprofile" class="btn btn-edit">
                            <button
                              type="button"
                              class="btn"
                              data-mdb-ripple-color="dark"
                            >
                              Chỉnh sửa
                            </button>
                          </router-link>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
const data = ref({});
const ID_DG = localStorage.getItem("ID_DG");
const fetchData = () => {
  axios
    .get("http://localhost:3000/authentication/info/" + ID_DG)
    .then((res) => {
      console.log("Data aaaaaaaaaa", res.data);
      data.value = res.data;
      console.log(data.value);
    })
    .catch((err) => console.log(err));
};
fetchData();
</script>
<style lang="scss" scoped>
@import "./Profile.scss";
</style>
