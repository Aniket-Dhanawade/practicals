Slip 9
Que1

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>String Manipulation Form</title>
</head>
<body>
    <h2>String Manipulation Form</h2>

    <form method="post" action="">
        <label for="inputString">Enter a string:</label>
        <input type="text" id="inputString" name="inputString" required>
        <br>

        <label for="separator">Choose a separator:</label>
        <select id="separator" name="separator" required>
            <option value="#">#</option>
            <option value="|">|</option>
            <option value="%">%</option>
        </select>
        <br>

        <button type="submit">Submit</button>
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        // Get user input
        $inputString = $_POST["inputString"];
        $chosenSeparator = $_POST["separator"];

        // Split the string into separate words using the given separator
        $words = explode($chosenSeparator, $inputString);

        // Replace all occurrences of separator in the given string with a different separator
        $newSeparator = ",";
        $modifiedString = str_replace($chosenSeparator, $newSeparator, $inputString);

        // Find the last word in the given string
        $lastWord = end($words);

        // Display the results
        echo "<h3>Results:</h3>";
        echo "<p>Original String: $inputString</p>";
        echo "<p>Separated Words: " . implode(", ", $words) . "</p>";
        echo "<p>Modified String: $modifiedString</p>";
        echo "<p>Last Word: $lastWord</p>";
    }
    ?>
</body>
</html>


-----------------------------------------------------------------------------------
que 2 A]

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Array Chart</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <h2>Random Array Chart</h2>

    <?php
    // Generate a random array of 50 integers
    $data = array_map('rand', array_fill(0, 50, 1), array_fill(0, 50, 100));

    // Convert the array to a JSON format for JavaScript
    $json_data = json_encode($data);
    ?>

    <canvas id="lineChart" width="400" height="200"></canvas>
    <canvas id="scatterPlot" width="400" height="200"></canvas>

    <script>
        // Parse the JSON data in JavaScript
        var data = <?php echo $json_data; ?>;

        // Line Chart
        var lineChartCanvas = document.getElementById('lineChart').getContext('2d');
        var lineChart = new Chart(lineChartCanvas, {
            type: 'line',
            data: {
                labels: Array.from({ length: data.length }, (_, i) => i + 1),
                datasets: [{
                    label: 'Line Chart',
                    data: data,
                    borderColor: 'rgba(75, 192, 192, 1)',
                    borderWidth: 2,
                    fill: false,
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: 'Index'
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: 'Value'
                        }
                    }
                }
            }
        });

        // Scatter Plot
        var scatterPlotCanvas = document.getElementById('scatterPlot').getContext('2d');
        var scatterPlot = new Chart(scatterPlotCanvas, {
            type: 'scatter',
            data: {
                labels: Array.from({ length: data.length }, (_, i) => i + 1),
                datasets: [{
                    label: 'Scatter Plot',
                    data: data,
                    backgroundColor: 'rgba(255, 99, 132, 1)',
                    borderColor: 'rgba(255, 99, 132, 1)',
                    borderWidth: 1,
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: 'Index'
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: 'Value'
                        }
                    }
                }
            }
        });
    </script>
</body>
</html>


-------------------------------------------------------------------------------------

Que2 B]

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Subject Marks Pie Chart</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <h2>Subject Marks Pie Chart</h2>

    <?php
    // Sample data for subjects and marks
    $subjects = ['Math', 'English', 'Science', 'History', 'Art'];
    $marks = [90, 80, 85, 75, 95];

    // Convert the arrays to JSON format for JavaScript
    $json_subjects = json_encode($subjects);
    $json_marks = json_encode($marks);
    ?>

    <canvas id="marksPieChart" width="400" height="200"></canvas>

    <script>
        // Parse the JSON data in JavaScript
        var subjects = <?php echo $json_subjects; ?>;
        var marks = <?php echo $json_marks; ?>;

        // Pie Chart
        var pieChartCanvas = document.getElementById('marksPieChart').getContext('2d');
        var pieChart = new Chart(pieChartCanvas, {
            type: 'pie',
            data: {
                labels: subjects,
                datasets: [{
                    data: marks,
                    backgroundColor: [
                        'rgba(255, 99, 132, 0.7)',
                        'rgba(54, 162, 235, 0.7)',
                        'rgba(255, 206, 86, 0.7)',
                        'rgba(75, 192, 192, 0.7)',
                        'rgba(153, 102, 255, 0.7)',
                    ],
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                title: {
                    display: true,
                    text: 'Subject-wise Marks Distribution'
                }
            }
        });
    </script>
</body>
</html>

-------------------------------------------------------------------------------------

que 2 C]

install pandas library using 
pip install pandas



import pandas as pd

# a) Import Dataset and Describing the dataset
dataset_path = "winequality-red.csv"
wine_data = pd.read_csv(dataset_path)

# Display descriptive statistics of the dataset
print("a) Describing the dataset:")
print(wine_data.describe())

# b) Shape of the dataset
print("\nb) Shape of the dataset:")
print(wine_data.shape)

# c) Display first 3 rows from dataset
print("\nc) Display first 3 rows from dataset:")
print(wine_data.head(3))



Csv file  save as winequality-red.csv

fixed acidity,volatile acidity,citric acid,residual sugar,chlorides,free sulfur dioxide,total sulfur dioxide,density,pH,sulphates,alcohol,quality
7.4,0.70,0.00,1.9,0.076,11.0,34.0,0.9978,3.51,0.56,9.4,5
7.8,0.88,0.00,2.6,0.098,25.0,67.0,0.9968,3.20,0.68,9.8,5
7.8,0.76,0.04,2.3,0.092,15.0,54.0,0.9970,3.26,0.65,9.8,5
