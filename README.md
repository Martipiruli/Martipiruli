<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Primos Click</title>
    <style>
        body {
            background-color: black;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-size: 10vw;
            margin: 0;
            font-family: 'Comic Sans MS', cursive, sans-serif; /* Peculiar Font */
        }
    </style>
</head>
<body>
    <div id="prime-number">2</div>

    <script>
        let primeNumbers = [2];
        let currentIndex = 0;

        function isPrime(num) {
            for (let i = 2; i <= Math.sqrt(num); i++) {
                if (num % i === 0) return false;
            }
            return num > 1;
        }

        function nextPrime() {
            let lastPrime = primeNumbers[primeNumbers.length - 1];
            let nextPrime = lastPrime + 1;
            while (!isPrime(nextPrime)) {
                nextPrime++;
            }
            primeNumbers.push(nextPrime);
        }

        function previousPrime() {
            if (currentIndex > 0) {
                currentIndex--;
                document.getElementById('prime-number').innerText = primeNumbers[currentIndex];
            }
        }

        document.body.addEventListener('click', function(event) {
            if (event.button === 0) { // Left click
                if (currentIndex === primeNumbers.length - 1) {
                    nextPrime();
                }
                currentIndex++;
                document.getElementById('prime-number').innerText = primeNumbers[currentIndex];
            }
        });

        document.body.addEventListener('contextmenu', function(event) {
            event.preventDefault();
            previousPrime();
        });
    </script>
</body>
</html>
