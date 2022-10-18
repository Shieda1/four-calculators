// https://calculator.swiftutors.com/straight-line-depreciation-calculator.html

const v1 =  document.getElementById('v1');
const v2 = document.getElementById('v2');
const v3 = document.getElementById('v3');
const btn = document.getElementById('btn');
const result = document.getElementById('result');

// radio buttons
const straightLineDepreciationRadio = document.getElementById('straightLineDepreciationRadio');
const assetValueRadio = document.getElementById('assetValueRadio');
const salvageValueRadio = document.getElementById('salvageValueRadio');
const usefulLifeinYearsRadio = document.getElementById('usefulLifeinYearsRadio');

let straightLineDepreciation;
let assetValue = v1;
let salvageValue = v2;
let usefulLifeinYears = v3;

// labels of the inpust
const variable1 = document.getElementById('variable1');
const variable2 = document.getElementById('variable2');
const variable3 = document.getElementById('variable3');

straightLineDepreciationRadio.addEventListener('click', function() {
  variable1.textContent = 'Asset Value';
  variable2.textContent = 'Salvage Value';
  variable3.textContent = 'Useful Life in Years';
  assetValue = v1;
  salvageValue = v2;
  usefulLifeinYears = v3;
  result.textContent = '';
});

assetValueRadio.addEventListener('click', function() {
  variable1.textContent = 'Straight Line Depreciation';
  variable2.textContent = 'Salvage Value';
  variable3.textContent = 'Useful Life in Years';
  straightLineDepreciation = v1;
  salvageValue = v2;
  usefulLifeinYears = v3;
  result.textContent = '';
});

salvageValueRadio.addEventListener('click', function() {
  variable1.textContent = 'Straight Line Depreciation';
  variable2.textContent = 'Asset Value';
  variable3.textContent = 'Useful Life in Years';
  straightLineDepreciation = v1;
  assetValue = v2;
  usefulLifeinYears = v3;
  result.textContent = '';
});

usefulLifeinYearsRadio.addEventListener('click', function() {
  variable1.textContent = 'Straight Line Depreciation';
  variable2.textContent = 'Asset Value';
  variable3.textContent = 'Salvage Value';
  straightLineDepreciation = v1;
  assetValue = v2;
  salvageValue = v3;
  result.textContent = '';
});

btn.addEventListener('click', function() {
  
  if(straightLineDepreciationRadio.checked)
    result.textContent = `Straight Line Depreciation = ${computeStraightLineDepreciation().toFixed(2)}`;

  else if(assetValueRadio.checked)
    result.textContent = `Asset Value = ${computeAssetValue().toFixed(2)}`;

  else if(salvageValueRadio.checked)
    result.textContent = `Salvage Value = ${computeSalvageValue().toFixed(2)}`;

  else if(usefulLifeinYearsRadio.checked)
    result.textContent = `Useful Life in Years = ${computeUsefulLifeinYears().toFixed(2)}`;
})

// calculation

function computeStraightLineDepreciation() {
  return (Number(assetValue.value) - Number(salvageValue.value)) / Number(usefulLifeinYears.value);
}

function computeAssetValue() {
  return (Number(straightLineDepreciation.value) * Number(usefulLifeinYears.value)) + Number(salvageValue.value);
}

function computeSalvageValue() {
  return Number(assetValue.value) - (Number(straightLineDepreciation.value) * Number(usefulLifeinYears.value));
}

function computeUsefulLifeinYears() {
  return (Number(assetValue.value) - Number(salvageValue.value)) / Number(straightLineDepreciation.value);
}