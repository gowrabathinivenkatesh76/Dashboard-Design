<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Analytics Dashboard</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f7fc;
    }
    .dashboard-container {
      max-width: 1200px;
      margin: 30px auto;
      background-color: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }
    .metrics {
      display: flex;
      justify-content: space-between;
      gap: 20px;
    }
    .metric-card {
      background-color: #007bff;
      color: white;
      padding: 20px;
      border-radius: 8px;
      width: 22%;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }
    .metric-card h3 {
      font-size: 2rem;
    }
    .metric-card p {
      font-size: 1.2rem;
    }
    .chart-container {
      display: flex;
      gap: 30px;
      margin-top: 30px;
    }
    .chart {
      flex: 1;
      background-color: #fff;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }
    .chart canvas {
      width: 100% !important;
      height: 300px !important;
    }
    .dropdown {
      margin-top: 20px;
    }
    .dropdown button {
      background-color: #007bff;
      color: white;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <div class="dashboard-container">
    <div class="metrics">
      <div class="metric-card">
        <h3 id="totalSales">5000</h3>
        <p>Total Sales</p>
      </div>
      <div class="metric-card">
        <h3 id="newUsers">230</h3>
        <p>New Users</p>
      </div>
      <div class="metric-card">
        <h3 id="conversionRate">4.5%</h3>
        <p>Conversion Rate</p>
      </div>
      <div class="metric-card">
        <h3 id="avgOrderValue">$85</h3>
        <p>Average Order Value</p>
      </div>
    </div>

    <div class="dropdown">
      <button class="btn btn-primary">Select Time Range</button>
    </div>

    <div class="chart-container">
      <div class="chart">
        <canvas id="salesChart"></canvas>
      </div>
      <div class="chart">
        <canvas id="userChart"></canvas>
      </div>
    </div>

  </div>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // Dummy Data
    const salesData = [100, 200, 300, 400, 500, 600, 700, 800, 900, 1000];
    const userData = [50, 60, 70, 80, 90, 100, 110, 120, 130, 140];

    // Sales Chart
    const ctx1 = document.getElementById('salesChart').getContext('2d');
    const salesChart = new Chart(ctx1, {
      type: 'line',
      data: {
        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct'],
        datasets: [{
          label: 'Sales',
          data: salesData,
          fill: false,
          borderColor: '#007bff',
          tension: 0.1
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: {
            display: false
          }
        },
        scales: {
          x: {
            grid: {
              display: false
            }
          },
          y: {
            beginAtZero: true
          }
        }
      }
    });

    // User Growth Chart
    const ctx2 = document.getElementById('userChart').getContext('2d');
    const userChart = new Chart(ctx2, {
      type: 'bar',
      data: {
        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct'],
        datasets: [{
          label: 'New Users',
          data: userData,
          backgroundColor: '#28a745',
          borderRadius: 5
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: {
            display: false
          }
        },
        scales: {
          x: {
            grid: {
              display: false
            }
          },
          y: {
            beginAtZero: true
          }
        }
      }
    });

    // Interactivity (for dropdown and data updates)
    document.querySelector('.dropdown button').addEventListener('click', function() {
      // Simulate changing time range
      alert('Time range changed to the last 3 months!');
    });

    // Update Key Metrics Example (This could be hooked into real data in a live environment)
    setInterval(() => {
      document.getElementById('totalSales').textContent = Math.floor(Math.random() * 10000);
      document.getElementById('newUsers').textContent = Math.floor(Math.random() * 500);
      document.getElementById('conversionRate').textContent = `${(Math.random() * 10).toFixed(2)}%`;
      document.getElementById('avgOrderValue').textContent = `$${(Math.random() * 200).toFixed(2)}`;
    }, 5000); // Update every 5 seconds
  </script>
</body>
</html>
