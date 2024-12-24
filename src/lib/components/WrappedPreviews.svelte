<style>
    .container {
      display: flex;
      justify-content: space-between;
      gap: 20px;
    }

    .card {
      width: 200px;
      height: 300px;
      perspective: 1000px;
    }

    .card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      transform-style: preserve-3d;
      transition: transform 0.6s;
    }

    .card:hover .card-inner {
      transform: rotateY(-180deg);
    }

    .card-front,
    .card-back {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      backface-visibility: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      font-size: 20px;
      color: white;
      border-radius: 8px;
    }

    .card-front {
      flex-direction: column;
      justify-content: flex-end;
    }

    .card-back {
      /*background-color: #2ecc71;*/
      transform: rotateY(-180deg);
      flex-direction: column;
      justify-content: flex;
      background: radial-gradient(circle, #ff0000 30%, transparent 30%),
              radial-gradient(circle, #ff6600 30%, transparent 30%),
              radial-gradient(circle, #ffff00 30%, transparent 30%),
              radial-gradient(circle, #00ff00 30%, transparent 30%),
              radial-gradient(circle, #0000ff 30%, transparent 30%),
              radial-gradient(circle, #6600ff 30%, transparent 30%);
  background-position: center, 30px 30px, -30px 30px, 30px -30px, -30px -30px, 60px 60px;
  background-repeat: no-repeat;
  background-size: 50% 50%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
    }

    .card button {
      padding: 10px 20px;
      background-color: white;
      color: black;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .card button:hover {
      background-color: #ecf0f1;
    }

    .card-left .card-front {
        text-align: right;
        background: linear-gradient(to bottom, #4305F3, #A5D7D8, #F9E32B, #C21C0B, black);
    }

    .card-right .card-front {
        text-align: left;
        background: radial-gradient(circle at right, black, #C21C0B, #F9E32B, #A5D7D8, #4305F3);
    }
  </style>

  <div class="container">
    <div class="card card-left">
      <div class="card-inner">
        <div class="card-front">
          <h2>Spotify Wrapped Classic</h2>
        </div>
        <div class="card-back">
          <p>Back Text 1</p>
          <button>Click Me</button>
        </div>
      </div>
    </div>

    <div class="card card-right">
      <div class="card-inner">
        <div class="card-front">
            <h2>Spotify Wrapped Extended</h2>
        </div>
        <div class="card-back">
          <p>Back Text 2</p>
          <button>Click Me</button>
        </div>
      </div>
    </div>
  </div>