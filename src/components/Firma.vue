<template>
    <div class="raiz">
        <canvas ref="canFirma" class="firma" width="380" height="200"></canvas>
        <div class="borde" @mousemove="desenhar" @mousedown.left="iniciarDesenho" @mousedown.right="iniciarBorracha" @mouseup="parar" @contextmenu.prevent>
        </div>
    </div>
</template>


<script>
export default {
    data() {
        return {
            ctx: null,
            x0: -1,
            y0: -1,
            desenhando: false
        }
    },
    methods: {
        iniciarDesenho() {
            this.ctx.strokeStyle = '#303030'
            this.ctx.lineWidth = 5
            this.desenhando = true
        },
        iniciarBorracha() {
            this.ctx.strokeStyle = '#fff'
            this.ctx.lineWidth = 20
            this.desenhando = true
        },
        parar() {
            this.desenhando = false
            this.x0 = -1
            this.y0 = -1
        },
        desenhar(event) {

            if (!this.desenhando) {
                return
            }

            if (this.x0 == -1 || this.y0 == -1) {
                this.x0 = event.offsetX
                this.y0 = event.offsetY
                return
            }

            const x1 = event.offsetX
            const y1 = event.offsetY

            this.ctx.beginPath()
            this.ctx.moveTo(this.x0, this.y0)
            this.ctx.lineTo(x1, y1)
            this.ctx.stroke()

            this.x0 = x1
            this.y0 = y1
        }
    },
    mounted() {
        this.ctx = this.$refs.canFirma.getContext('2d')        
        this.ctx.lineCap = 'round'
    }
}
</script>

<style>



.raiz {
    display: grid;
    margin: 10px;
}

.borde {
    cursor: pointer;
    border-radius: 5px;
    box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.9); 
    width: 380;
    height: 200px;

    grid-row: 1;
    grid-column: 1;
    z-index: 3;
}

.firma {
    cursor: pointer;
    background-color: white;
    border-radius: 5px;

    grid-row: 1;
    grid-column: 1;
    z-index: 2;
}
    
</style>