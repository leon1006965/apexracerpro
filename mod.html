<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Apex Racer Pro</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Rajdhani:wght@600;800&display=swap');

        body { margin: 0; overflow: hidden; background: #000; font-family: 'Rajdhani', sans-serif; touch-action: none; user-select: none; }
        
        #hud {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            z-index: 10;
        }

        .top-ui {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            background: linear-gradient(180deg, rgba(0,0,0,0.8) 0%, transparent 100%);
        }

        .btn-group { display: flex; gap: 10px; pointer-events: auto; }

        .mode-btn, .mod-trigger {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255,255,255,0.2);
            color: #fff;
            padding: 8px 15px;
            border-radius: 5px;
            font-weight: 800;
            text-transform: uppercase;
            cursor: pointer;
            font-size: 13px;
            transition: all 0.2s;
        }
        .mode-btn.active { background: #e74c3c; border-color: #e74c3c; }
        .mod-trigger { background: #f1c40f; color: #000; border: none; }

        /* Mod Menu Modal */
        #mod-menu {
            position: absolute;
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 250px;
            background: rgba(0, 0, 0, 0.95);
            border: 2px solid #f1c40f;
            border-radius: 10px;
            padding: 20px;
            display: none;
            pointer-events: auto;
            z-index: 100;
            color: white;
            text-align: center;
        }
        .mod-option {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 15px 0;
            font-weight: 800;
            font-size: 18px;
        }
        /* Toggle Switch */
        .switch {
            position: relative;
            display: inline-block;
            width: 50px;
            height: 24px;
        }
        .switch input { opacity: 0; width: 0; height: 0; }
        .slider {
            position: absolute;
            cursor: pointer;
            top: 0; left: 0; right: 0; bottom: 0;
            background-color: #444;
            transition: .4s;
            border-radius: 24px;
        }
        .slider:before {
            position: absolute;
            content: "";
            height: 18px; width: 18px;
            left: 3px; bottom: 3px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }
        input:checked + .slider { background-color: #f1c40f; }
        input:checked + .slider:before { transform: translateX(26px); }

        /* Speedo */
        .stats {
            position: absolute;
            top: 80px;
            left: 20px;
            color: white;
        }
        #speed-num { font-size: 60px; font-weight: 800; line-height: 1; }
        .unit { font-size: 14px; color: #e74c3c; letter-spacing: 2px; }

        /* JOYSTICK */
        #joystick-container {
            position: absolute;
            bottom: 50px;
            left: 50px;
            width: 150px;
            height: 150px;
            background: rgba(255,255,255,0.05);
            border: 2px solid rgba(255,255,255,0.1);
            border-radius: 50%;
            pointer-events: auto;
            backdrop-filter: blur(5px);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        #joystick-knob {
            width: 60px;
            height: 60px;
            background: #fff;
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(255,255,255,0.4);
            position: absolute;
        }
        
        .hint {
            position: absolute;
            bottom: 20px;
            width: 100%;
            text-align: center;
            color: rgba(255,255,255,0.3);
            font-size: 10px;
            letter-spacing: 2px;
            text-transform: uppercase;
        }
    </style>
</head>
<body>

    <div id="hud">
        <div class="top-ui">
            <div style="font-weight:800; font-size: 22px; color:#fff;">APEX <span style="color:#e74c3c">RACER PRO</span></div>
            <div class="btn-group">
                <button class="mode-btn active" id="btn-track" onclick="Game.loadLevel('track')">Circuit</button>
                <button class="mode-btn" id="btn-city" onclick="Game.loadLevel('city')">City</button>
                <button class="mod-trigger" onclick="Game.toggleModMenu()">MODS</button>
            </div>
        </div>

        <div id="mod-menu">
            <h2 style="margin-top:0; color:#f1c40f;">MOD MENU</h2>
            <div class="mod-option">
                <span>NOCLIP</span>
                <label class="switch">
                    <input type="checkbox" id="mod-noclip" onchange="Game.updateMods()">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="mod-option">
                <span>SUPER SPEED</span>
                <label class="switch">
                    <input type="checkbox" id="mod-speed" onchange="Game.updateMods()">
                    <span class="slider"></span>
                </label>
            </div>
            <button class="mode-btn" style="width:100%; margin-top:10px;" onclick="Game.toggleModMenu()">CLOSE</button>
        </div>

        <div class="stats">
            <div id="speed-num">0</div>
            <div class="unit">KM/H</div>
        </div>

        <div id="joystick-container">
            <div id="joystick-knob"></div>
        </div>

        <div class="hint">Use Joystick to Drive • Drag Screen to Look</div>
    </div>

    <script>
        const TextureGen = {
            carTexture: function() {
                const canvas = document.createElement('canvas');
                canvas.width = 512; canvas.height = 512;
                const ctx = canvas.getContext('2d');
                ctx.fillStyle = '#111'; ctx.fillRect(0,0,512,512);
                ctx.fillStyle = '#e74c3c'; ctx.fillRect(200, 0, 112, 512);
                ctx.fillStyle = '#222'; ctx.fillRect(0, 450, 512, 62);
                ctx.fillStyle = '#fff'; ctx.fillRect(50, 480, 80, 20); ctx.fillRect(382, 480, 80, 20);
                return new THREE.CanvasTexture(canvas);
            },
            asphalt: function() {
                const c = document.createElement('canvas');
                c.width = 256; c.height = 256;
                const ctx = c.getContext('2d');
                ctx.fillStyle = '#222'; ctx.fillRect(0,0,256,256);
                for(let i=0; i<5000; i++) {
                    ctx.fillStyle = Math.random() > 0.5 ? '#282828' : '#1c1c1c';
                    ctx.fillRect(Math.random()*256, Math.random()*256, 2, 2);
                }
                const t = new THREE.CanvasTexture(c);
                t.wrapS = t.wrapT = THREE.RepeatWrapping;
                t.repeat.set(15, 15);
                return t;
            }
        };

        const Game = {
            scene: null, camera: null, renderer: null, car: null,
            obstacles: [],
            joystick: { x: 0, y: 0, active: false },
            physics: { speed: 0, rot: 0, maxSpeed: 0.7, accel: 0.012, friction: 0.98 },
            mods: { noclip: false, superSpeed: false },
            
            init: function() {
                this.scene = new THREE.Scene();
                this.scene.background = new THREE.Color(0x87ceeb);
                this.scene.fog = new THREE.Fog(0x87ceeb, 20, 200);

                this.camera = new THREE.PerspectiveCamera(60, window.innerWidth/window.innerHeight, 0.1, 1000);
                
                this.renderer = new THREE.WebGLRenderer({ antialias: true });
                this.renderer.setSize(window.innerWidth, window.innerHeight);
                this.renderer.shadowMap.enabled = true;
                document.body.appendChild(this.renderer.domElement);

                const light = new THREE.DirectionalLight(0xffffff, 1.2);
                light.position.set(50, 100, 50);
                light.castShadow = true;
                this.scene.add(light);
                this.scene.add(new THREE.AmbientLight(0xffffff, 0.5));

                this.buildCar();
                this.loadLevel('track');
                this.setupJoystick();
                
                window.addEventListener('resize', () => {
                    this.camera.aspect = window.innerWidth / window.innerHeight;
                    this.camera.updateProjectionMatrix();
                    this.renderer.setSize(window.innerWidth, window.innerHeight);
                });

                this.loop();
            },

            toggleModMenu: function() {
                const menu = document.getElementById('mod-menu');
                menu.style.display = (menu.style.display === 'block') ? 'none' : 'block';
            },

            updateMods: function() {
                this.mods.noclip = document.getElementById('mod-noclip').checked;
                this.mods.superSpeed = document.getElementById('mod-speed').checked;
                
                // Real-time physics update
                if(this.mods.superSpeed) {
                    this.physics.maxSpeed = 3.5;
                    this.physics.accel = 0.2;
                } else {
                    this.physics.maxSpeed = 0.7;
                    this.physics.accel = 0.012;
                }
            },

            buildCar: function() {
                this.car = new THREE.Group();
                const bodyMat = new THREE.MeshStandardMaterial({ map: TextureGen.carTexture(), metalness: 0.5, roughness: 0.2 });
                const body = new THREE.Mesh(new THREE.BoxGeometry(2, 0.7, 4.5), bodyMat);
                body.position.y = 0.6;
                body.castShadow = true;
                this.car.add(body);

                const cabin = new THREE.Mesh(new THREE.BoxGeometry(1.6, 0.6, 2.2), new THREE.MeshStandardMaterial({color: 0x000000}));
                cabin.position.set(0, 1.2, -0.2);
                this.car.add(cabin);

                const wheelGeo = new THREE.CylinderGeometry(0.4, 0.4, 0.4, 24);
                wheelGeo.rotateZ(Math.PI/2);
                const wPos = [[0.9, 1.4], [-0.9, 1.4], [0.9, -1.4], [-0.9, -1.4]];
                this.wheels = [];
                wPos.forEach(p => {
                    const w = new THREE.Mesh(wheelGeo, new THREE.MeshStandardMaterial({color: 0x111111}));
                    w.position.set(p[0], 0.4, p[1]);
                    this.car.add(w);
                    this.wheels.push(w);
                });
                this.scene.add(this.car);
            },

            loadLevel: function(type) {
                this.obstacles.forEach(o => this.scene.remove(o));
                this.obstacles = [];
                if(this.floor) this.scene.remove(this.floor);

                document.getElementById('btn-track').classList.toggle('active', type === 'track');
                document.getElementById('btn-city').classList.toggle('active', type === 'city');

                this.floor = new THREE.Mesh(new THREE.PlaneGeometry(1000, 1000), new THREE.MeshStandardMaterial({map: TextureGen.asphalt()}));
                this.floor.rotation.x = -Math.PI/2;
                this.floor.receiveShadow = true;
                this.scene.add(this.floor);

                if(type === 'track') {
                    this.createWall(20, 2, 300, 15, 1, 0);
                    this.createWall(20, 2, 300, -15, 1, 0);
                } else {
                    for(let i=0; i<30; i++) {
                        this.createWall(10, 20, 10, Math.random()*200-100, 10, Math.random()*200-100);
                    }
                }
                this.car.position.set(0, 0, 0);
                this.physics.speed = 0;
            },

            createWall: function(w, h, d, x, y, z) {
                const mesh = new THREE.Mesh(new THREE.BoxGeometry(w, h, d), new THREE.MeshStandardMaterial({color: 0x333333}));
                mesh.position.set(x, y, z);
                mesh.userData.bbox = new THREE.Box3().setFromObject(mesh);
                this.scene.add(mesh);
                this.obstacles.push(mesh);
            },

            setupJoystick: function() {
                const container = document.getElementById('joystick-container');
                const knob = document.getElementById('joystick-knob');
                const rect = container.getBoundingClientRect();
                const centerX = rect.left + rect.width / 2;
                const centerY = rect.top + rect.height / 2;

                const handleMove = (e) => {
                    if(!this.joystick.active) return;
                    const touch = e.touches ? e.touches[0] : e;
                    let dx = touch.clientX - centerX;
                    let dy = touch.clientY - centerY;
                    const dist = Math.sqrt(dx*dx + dy*dy);
                    const max = 60;
                    if(dist > max) { dx *= max/dist; dy *= max/dist; }
                    knob.style.transform = `translate(${dx}px, ${dy}px)`;
                    this.joystick.x = dx / max;
                    this.joystick.y = -dy / max;
                };

                container.addEventListener('touchstart', (e) => { this.joystick.active = true; handleMove(e); });
                window.addEventListener('touchmove', handleMove);
                window.addEventListener('touchend', () => {
                    this.joystick.active = false;
                    this.joystick.x = 0; this.joystick.y = 0;
                    knob.style.transform = `translate(0px, 0px)`;
                });
                container.addEventListener('mousedown', () => this.joystick.active = true);
                window.addEventListener('mousemove', handleMove);
                window.addEventListener('mouseup', () => {
                    this.joystick.active = false;
                    this.joystick.x = 0; this.joystick.y = 0;
                    knob.style.transform = `translate(0px, 0px)`;
                });
            },

            checkCollision: function(pos) {
                if(this.mods.noclip) return false; // Noclip Mod
                const carBox = new THREE.Box3().setFromCenterAndSize(pos, new THREE.Vector3(2, 1, 4.5));
                for(let o of this.obstacles) {
                    if(carBox.intersectsBox(o.userData.bbox)) return true;
                }
                return false;
            },

            loop: function() {
                requestAnimationFrame(() => this.loop());

                if(Math.abs(this.joystick.y) > 0.1) {
                    this.physics.speed += this.joystick.y * this.physics.accel;
                } else {
                    this.physics.speed *= this.physics.friction;
                }

                this.physics.speed = Math.max(-this.physics.maxSpeed/2, Math.min(this.physics.maxSpeed, this.physics.speed));

                if(Math.abs(this.physics.speed) > 0.05) {
                    this.physics.rot -= this.joystick.x * 0.04 * (this.physics.speed > 0 ? 1 : -1);
                }

                const nextPos = this.car.position.clone();
                nextPos.x += Math.sin(this.physics.rot) * this.physics.speed;
                nextPos.z += Math.cos(this.physics.rot) * this.physics.speed;

                if(!this.checkCollision(nextPos)) {
                    this.car.position.copy(nextPos);
                } else {
                    this.physics.speed *= -0.4;
                }

                this.car.rotation.y = this.physics.rot;
                this.wheels.forEach(w => w.rotation.x += this.physics.speed * 0.5);

                const camOffset = new THREE.Vector3(0, 4, -10).applyMatrix4(this.car.matrixWorld);
                this.camera.position.lerp(camOffset, 0.1);
                this.camera.lookAt(this.car.position);

                document.getElementById('speed-num').innerText = Math.round(Math.abs(this.physics.speed * 180));
                this.renderer.render(this.scene, this.camera);
            }
        };

        window.onload = () => Game.init();
    </script>
</body>
</html>
