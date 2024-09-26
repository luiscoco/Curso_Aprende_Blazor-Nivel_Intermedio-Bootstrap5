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

## 2. Create a new razor component to include a Bootstrap Accordion in our Blazor Application 

Right click on the Pages folder and select the menu option Add->New Razor Component

Set the new component name

Input the component code:

```razor
@page "/accordion"

<h3>Accordion Example with Collapse/Expand Buttons</h3>

<!-- Accordion Component -->
<div class="accordion" id="accordionExample">
    <div class="accordion-item">
        <h2 class="accordion-header" id="headingOne">
            <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                Accordion Item #1
            </button>
        </h2>
        <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                This is the first item's accordion body.
            </div>
        </div>
    </div>
    <div class="accordion-item">
        <h2 class="accordion-header" id="headingTwo">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                Accordion Item #2
            </button>
        </h2>
        <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                This is the second item's accordion body.
            </div>
        </div>
    </div>
    <div class="accordion-item">
        <h2 class="accordion-header" id="headingThree">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                Accordion Item #3
            </button>
        </h2>
        <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                This is the third item's accordion body.
            </div>
        </div>
    </div>
</div>

@code {

}
```

## 3. Create in the NavMenu a new Navlink for navigating to this new component 

Open the NavMenu.razor and add this new Navlink below the Weather one:

```razor
<div class="nav-item px-3">
    <NavLink class="nav-link" href="accordion">
        <span class="bi bi-list-nested-nav-menu" aria-hidden="true"></span> Accordion
    </NavLink>
</div>
```

## 4. Run the application and see the result

We navigate to the Accordion component selected the menu option and the you can click on the Accordion Items to collapse or expan them

![image](https://github.com/user-attachments/assets/57dc824a-1df8-4fd7-b7d1-04997c1fe85b)

## 5. Now create two buttons for Expand or Collapse all the Accordion Items

In the Accordion.razor component include this code: 

```razor
@page "/accordion"
@inject IJSRuntime JS

<h3>Accordion Example with Collapse/Expand Buttons</h3>

<!-- Buttons to Collapse/Expand the Accordion -->
<div class="mb-3">
    <button class="btn btn-primary" @onclick="ExpandAll">Expand All</button>
    <button class="btn btn-secondary" @onclick="CollapseAll">Collapse All</button>
</div>

<!-- Accordion Component -->
<div class="accordion" id="accordionExample">
    <div class="accordion-item">
        <h2 class="accordion-header" id="headingOne">
            <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                Accordion Item #1
            </button>
        </h2>
        <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                This is the first item's accordion body.
            </div>
        </div>
    </div>
    <div class="accordion-item">
        <h2 class="accordion-header" id="headingTwo">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                Accordion Item #2
            </button>
        </h2>
        <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                This is the second item's accordion body.
            </div>
        </div>
    </div>
    <div class="accordion-item">
        <h2 class="accordion-header" id="headingThree">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                Accordion Item #3
            </button>
        </h2>
        <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                This is the third item's accordion body.
            </div>
        </div>
    </div>
</div>

@code {
    private async Task ExpandAll()
    {
        await JS.InvokeVoidAsync("toggleAccordion", "expand");
    }

    private async Task CollapseAll()
    {
        await JS.InvokeVoidAsync("toggleAccordion", "collapse");
    }
}
```

## 6. Create a new JavaScript file accordion.js

Include this code in the accordion.js file in order to expand and collapse the accordion items:

```javascript
function toggleAccordion(action) {
    let accordionItems = document.querySelectorAll('.accordion-collapse');

    accordionItems.forEach(item => {
        if (action === 'collapse') {
            item.classList.remove('show');  // Collapse all
        } else if (action === 'expand') {
            item.classList.add('show');  // Expand all
        }
    });
}
```

See the application structure

![image](https://github.com/user-attachments/assets/c30f2cb7-3a14-4399-ae46-585512e3a76f)

## 7. Modify the App.razor to include a refernce to the accordion.js file

```
<script src="accordion.js"></script>
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
    <script src="accordion.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>

</html>
```

## 8. Run the application and see the results

We first press in the **Expand All** button 

![image](https://github.com/user-attachments/assets/735b3b94-7c9a-48b0-9e00-aa34010f0da1)

Then we press in the **Collapse All** button

![image](https://github.com/user-attachments/assets/2739ffe2-3b54-492c-a617-43709492c8fd)
