# How to install bootstrap 5 Components in your Blazor Web Application

For more information about **bootstrap 5** components visit this URL: https://getbootstrap.com/docs/5.0/getting-started/introduction/

See information about the **accordion** component in this URL: https://getbootstrap.com/docs/5.0/components/accordion/

See information about the **navbar** component in this URL: https://getbootstrap.com/docs/5.0/components/navbar/

## 1. Modify the App.razor

Include a new line for the **bootstrap 5** style reference in the App.razor **head** HTML element:

```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
```

Also include the **bootstrap 5** script in the App.razor **body** HTML element:

```
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
```

This is the whole App.razor code:

```razor
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <base href="/" />
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="icon" type="image/png" href="favicon.png" />
    <link rel="stylesheet" href="app.css" />
    <link rel="stylesheet" href="bootstrap5Samples.styles.css" />
    <HeadOutlet @rendermode="InteractiveServer" />
</head>

<body>
    <Routes @rendermode="InteractiveServer" />
    <script src="_framework/blazor.web.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>

</html>
```

## 2. 
