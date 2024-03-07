var radar = document.getElementById("radar");
var radarItems = document.getElementsByClassName("radarItem");
var radarSettings = {};

radarSettings.shape = "circle";
radarSettings.color = "blue";
radarSettings.borderColor = "white";
radarSettings.itemColor = "white";
radarSettings.size = 200;
radarSettings.zoom = 0.5;
radarSettings.opacity = 0.8;
radarSettings.position = "bottom-right";

function applyRadarSettings() {
  if (radarSettings.shape == "circle") {
    radar.style.borderRadius = "50%";
  } else if (radarSettings.shape == "square") {
    radar.style.borderRadius = "0%";
  }
  radar.style.backgroundColor = radarSettings.color;
  radar.style.borderColor = radarSettings.borderColor;
  radar.style.width = radarSettings.size + "px";
  radar.style.height = radarSettings.size + "px";
  radar.style.transform = "scale(" + radarSettings.zoom + ")";
  radar.style.opacity = radarSettings.opacity;
  if (radarSettings.position == "bottom-right") {
    radar.style.right = "10px";
    radar.style.bottom = "10px";
  } else if (radarSettings.position == "bottom-left") {
    radar.style.left = "10px";
    radar.style.bottom = "10px";
  } else if (radarSettings.position == "top-right") {
    radar.style.right = "10px";
    radar.style.top = "10px";
  } else if (radarSettings.position == "top-left") {
    radar.style.left = "10px";
    radar.style.top = "10px";
  }
  radar.style.zIndex = "1000";

  for (var i = 0; i < radarItems.length; i++) {
    var item = radarItems[i];
    item.style.backgroundColor = radarSettings.itemColor;
  }
}

applyRadarSettings();

var settingsButton = document.createElement("button");
settingsButton.innerHTML = "Radar Settings";
settingsButton.style.position = "absolute";
settingsButton.style.right = "10px";
settingsButton.style.bottom = "220px";
settingsButton.style.zIndex = "1000";
settingsButton.onclick = function() {
  toggleSettingsMenu();
};
document.body.appendChild(settingsButton);

var settingsMenu = document.createElement("div");
settingsMenu.style.position = "absolute";
settingsMenu.style.right = "10px";
settingsMenu.style.bottom = "250px";
settingsMenu.style.width = "300px";
settingsMenu.style.height = "400px";
settingsMenu.style.backgroundColor = "black";
settingsMenu.style.color = "white";
settingsMenu.style.border = "2px solid white";
settingsMenu.style.zIndex = "1000";
settingsMenu.style.display = "none";
document.body.appendChild(settingsMenu);

var settingsTitle = document.createElement("h3");
settingsTitle.innerHTML = "Radar Settings";
settingsTitle.style.textAlign = "center";
settingsMenu.appendChild(settingsTitle);

var shapeLabel = document.createElement("label");
shapeLabel.innerHTML = "Shape: ";
settingsMenu.appendChild(shapeLabel);

var shapeSelect = document.createElement("select");
var shapeOptions = ["circle", "square"];
for (var i = 0; i < shapeOptions.length; i++) {
  var option = document.createElement("option");
  option.value = shapeOptions[i];
  option.text = shapeOptions[i];
  shapeSelect.appendChild(option);
}
settingsMenu.appendChild(shapeSelect);

shapeSelect.onchange = function() {
  radarSettings.shape = shapeSelect.value;
  applyRadarSettings();
};

var colorLabel = document.createElement("label");
colorLabel.innerHTML = "Color: ";
settingsMenu.appendChild(colorLabel);

var colorInput = document.createElement("input");
colorInput.type = "color";
colorInput.value = "#0000FF";
settingsMenu.appendChild(colorInput);

colorInput.onchange = function() {
  radarSettings.color = colorInput.value;
  applyRadarSettings();
};

var borderColorLabel = document.createElement("label");
borderColorLabel.innerHTML = "Border Color: ";
settingsMenu.appendChild(borderColorLabel);

var borderColorInput = document.createElement("input");
borderColorInput.type = "color";
borderColorInput.value = "#FFFFFF";
settingsMenu.appendChild(borderColorInput);

borderColorInput.onchange = function() {
  radarSettings.borderColor = borderColorInput.value;
  applyRadarSettings();
};

var itemColorLabel = document.createElement("label");
itemColorLabel.innerHTML = "Item Color: ";
settingsMenu.appendChild(itemColorLabel);

var itemColorInput = document.createElement("input");
itemColorInput.type = "color";
itemColorInput.value = "#FFFFFF";
settingsMenu.appendChild(itemColorInput);

itemColorInput.onchange = function() {
  radarSettings.itemColor = itemColorInput.value;
  applyRadarSettings();
};

var sizeLabel = document.createElement("label");
sizeLabel.innerHTML = "Size: ";
settingsMenu.appendChild(sizeLabel);

var sizeRange = document.createElement("input");
sizeRange.type = "range";
sizeRange.min = "100";
sizeRange.max = "300";
sizeRange.value = "200";
settingsMenu.appendChild(sizeRange);

sizeRange.oninput = function() {
  radarSettings.size = sizeRange.value;
  applyRadarSettings();
};

var zoomLabel = document.createElement("label");
zoomLabel.innerHTML = "Zoom: ";
settingsMenu.appendChild(zoomLabel);

var zoomRange = document.createElement("input");
zoomRange.type = "range";
zoomRange.min = "0.1";
zoomRange.max = "1";
zoomRange.step = "0.1";
zoomRange.value = "0.5";
settingsMenu.appendChild(zoomRange);

zoomRange.oninput = function() {
  radarSettings.zoom = zoomRange.value;
  applyRadarSettings();
};

var opacityLabel = document.createElement("label");
opacityLabel.innerHTML = "Opacity: ";
settingsMenu.appendChild(opacityLabel);

var opacityRange = document.createElement("input");
opacityRange.type = "range";
opacityRange.min = "0";
opacityRange.max = "1";
opacityRange.step = "0.1";
opacityRange.value = "0.8";
settingsMenu.appendChild(opacityRange);

opacityRange.oninput = function() {
  radarSettings.opacity = opacityRange.value;
  applyRadarSettings();
};

var positionLabel = document.createElement("label");
positionLabel.innerHTML = "Position: ";
settingsMenu.appendChild(positionLabel);

var positionSelect = document.createElement("select");
var positionOptions = ["bottom-right", "bottom-left", "top-right", "top-left"];
for (var i = 0; i < positionOptions.length; i++) {
  var option = document.createElement("option");
  option.value = positionOptions[i];
  option.text = positionOptions[i];
  positionSelect.appendChild(option);
}
settingsMenu.appendChild(positionSelect);

positionSelect.onchange = function() {
  radarSettings.position = positionSelect.value;
  applyRadarSettings();
};

function toggleSettingsMenu() {
  if (settingsMenu.style.display == "none") {
    settingsMenu.style.display = "block";
  } else {
    settingsMenu.style.display = "none";
  }
}
