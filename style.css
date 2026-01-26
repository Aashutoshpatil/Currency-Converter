const dropdowns = document.querySelectorAll("select");
const btn = document.querySelector("button");
const fromCurr = document.querySelector("select[name='from']");
const toCurr = document.querySelector("select[name='to']");
const msg = document.querySelector(".msg");

/* Populate dropdowns */
dropdowns.forEach((select) => {
  for (let code in countryList) {
    let option = document.createElement("option");
    option.value = code;
    option.innerText = code;

    if (select.name === "from" && code === "USD") option.selected = true;
    if (select.name === "to" && code === "INR") option.selected = true;

    select.append(option);
  }

  select.addEventListener("change", () => updateFlag(select));
});

/* Update flag */
function updateFlag(select) {
  const img = select.previousElementSibling;
  img.src = `https://flagsapi.com/${countryList[select.value]}/flat/64.png`;
}

/* Fetch exchange rate (FRANKFURTER API) */
async function updateExchangeRate() {
  const amount = document.querySelector("input").value || 1;

  const url = `https://api.frankfurter.app/latest?amount=${amount}&from=${fromCurr.value}&to=${toCurr.value}`;

  try {
    const response = await fetch(url);
    const data = await response.json();

    const rate = data.rates[toCurr.value];
    msg.innerText = `${amount} ${fromCurr.value} = ${rate} ${toCurr.value}`;
  } catch (err) {
    msg.innerText = "Failed to fetch exchange rate ❌";
    console.error(err);
  }
}

/* Button click */
btn.addEventListener("click", (e) => {
  e.preventDefault();
  updateExchangeRate();
});

/* On load */
window.onload = updateExchangeRate;



//   description of this project for resume 
//  “Built a responsive Currency Converter web app using HTML,
//  CSS, and JavaScript, integrating live
//  exchange rate API with dynamic currency 
// flags and real-time conversion functionality.”
