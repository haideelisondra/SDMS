<template>
  <!-- begin app-main -->
  <div class="app-main" id="main">
    <!-- begin container-fluid -->
    <div class="container-fluid">
      <!-- begin row for breadcrumb and title -->
      <div class="row mb-4">
        <div class="col-12">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item" style="padding: 5px">Application</li>
              <li class="breadcrumb-item active" aria-current="page">List</li>
            </ol>
          </nav>
        </div>
      </div>
      <!-- end row for breadcrumb and title -->
      <div class="col-12 col-lg-6">
        <div class="card card-statistics">
          <div class="card-header">
            <div class="card-heading">
              <h1 class="display-4">Application Status</h1>
            </div>
          </div>
          <div class="card-body">
            <div class="table-responsive">
              <table class="table table-striped table-dark mb-0">
                <thead>
                  <tr>
                    <th scope="col">Title</th>
                    <th scope="col">Description</th>
                    <th scope="col">Status</th>
                    <th scope="col">Action</th>
                  </tr>
                </thead>
                <tbody>
                  <!-- Loop through applications and display them -->
                  <tr v-for="application in applications" :key="application.id">
                    <td>{{ application.scholarship.scholarship_name }}</td> <!-- Accessing the related scholarship name -->
                    <td>{{ application.scholarship.scholarship_description }}</td>
                    <td>
                      <span :class="{
                        'badge-success': application.status === 'accepted',
                        'badge-danger': application.status === 'rejected'
                      }" class="badge">
                        {{ application.status }}
                      </span>
                    </td>
                    <td>
                      <button 
                        class="btn btn-secondary"
                        :disabled="application.status !== 'accepted' && application.status !== 'rejected'">
                        Review
                      </button>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- end container-fluid -->
  </div>
  <!-- end app-main -->
</template>

<script>
export default {
  props: {
    applications: {
      type: Array,
      required: true,
    }
  },
};
</script>

<style scoped>
/* Add your custom styles here */
</style>
