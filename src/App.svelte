<script>
	let city = "";
	let weather = "";
	let temp = "";
	let humidity = "";
	let windspeed = "";

	const inputHandler = function () {
		
		fetch("https://api.openweathermap.org/data/2.5/weather?q=" + city + "&appid=19ba7f75471987de6887b8f7812d12f0")
			.then((response) => {
				return response.json();
			})
			.then((data) => {
				console.log(data);
				weather = data.weather[0].description;
				humidity = data.main.humidity;
				windspeed = data.wind.speed;
				temp = data.main.temp - 273.15 ;
				
			})
			.catch((err) => {
				weather = "city not found";
			});
	};
	
	
  
</script>

<main>
	s
	<div class="container">
		<div class="container2">
			<div class="A">
				<p colspan="3">
					<input class="display-box" type="text"  bind:value={city} />
				</p>
				<p><button on:click={inputHandler} /></p>
			</div>
			<div class="B">
				<p><span id="time" /></p>
			</div>
			<div class="C">
				<h1>
					<img
						src="https://thumbs.dreamstime.com/b/weather-forecast-app-icon-clouds-simple-vector-illustration-167505503.jpg"
						alt="add_alttext"
						height="40px"
						width="40px"
					/>
				</h1>
				<h1><span id="temp" />{temp}</h1>
			</div>
			<div class="D">
				<h1><span id="weather" />{weather}</h1>
			</div>
			<div class="E">
				<div class="E1">
					<p>humidity</p>
					<p>{humidity}</p>
				</div>
				<div class="E2">
					<p>windspeed</p>
					<p>{windspeed}</p>
				</div>
			</div>
		</div>
	</div>
</main>

<style>
	.container {
		display: flex;
		text-align: center;
		justify-content: center;
		font-family: "Times New Roman", Times, serif;
	}
	.container2 {
		background-color: #f1f2f5;
		min-height: 100px;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		font-size: 20px;
		color: rgba(11, 9, 9, 0.966);
	}
	.A {
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.B {
		display: flex;
		align-items: center;
	}
	.C {
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.D {
		display: flex;
		align-items: center;
	}
	.E {
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.E1 {
		display: flex;
		margin: 10px;
		flex-direction: column;
		align-items: left;
	}
	.E2 {
		display: flex;
		margin: 10px;
		flex-direction: column;
		align-items: right;
	}
	h1 {
		display: flex;
		justify-content: space-between;
		padding: 10px;
	}
</style>
