<template>

</template>

<script>

    window.addEventListener('load', () => {
    const el1 = document.getElementById('el1')
    const el2 = document.getElementById('el2')
    const el3 = document.getElementById('el3')
    const el4 = document.getElementById('el4')
    const size = 50
    const canvas = document.getElementById('canvas')
    const context = canvas.getContext("2d")
    let width = canvas.width = innerWidth
    let height = canvas.height = innerHeight

    context.strokeStyle = '#2f80ed'
    context.setLineDash([7,5])
    context.fillStyle = '#2f80ed'
    context.fillStyle = '#2f80ed38'
    /*------------------------------------*/
    let current = null;
    const elements = {
        el1: {
            x: Math.random() * (width - size),
            y: Math.random() * (height - size),
            startX: 0,
            startY: 0
        },
        el2: {
            x: Math.random() * (width - size),
            y: Math.random() * (height - size),
            startX: 0,
            startY: 0
        },
        el3: {
            x: Math.random() * (width - size),
            y: Math.random() * (height - size),
            startX: 0,
            startY: 0
        },
        el4: {
            x: Math.random() * (width - size),
            y: Math.random() * (height - size),
            startX: 0,
            startY: 0
        },
    }

    // начальное положение
    translate(el1, elements.el1.x, elements.el1.y)
    translate(el2, elements.el2.x, elements.el2.y)
    translate(el3, elements.el3.x, elements.el3.y)
    translate(el4, elements.el4.x, elements.el4.y)
    drawLine(
        elements.el1.x,
        elements.el2.x,
        elements.el1.y,
        elements.el2.y,
        elements.el3.x,
        elements.el4.x,
        elements.el3.y,
        elements.el4.y
    )
    

    /*------------------------------------*/

    el1.addEventListener('mousedown', onMouseDown)
    el2.addEventListener('mousedown', onMouseDown)
    el3.addEventListener('mousedown', onMouseDown)
    el4.addEventListener('mousedown', onMouseDown)




function onMouseDown(e) {
    e.preventDefault()
    // координаты нажатия мыши внутри элемента
    elements[e.target.id].startX = e.x - elements[e.target.id].x
    elements[e.target.id].startY = e.y - elements[e.target.id].y

    current = e.target

    document.body.addEventListener('mousemove', onMouseMove)
    document.body.addEventListener('mouseup', onMouseUp)
}

function onMouseMove(e) {
    const x = elements[current.id].x = e.x - elements[current.id].startX
    const y = elements[current.id].y = e.y - elements[current.id].startY

    translate(current, x, y)
    drawLine(
        elements.el1.x,
        elements.el2.x,
        elements.el1.y,
        elements.el2.y,
        elements.el3.x,
        elements.el4.x,
        elements.el3.y,
        elements.el4.y,
    )
}

function onMouseUp() {
    document.body.removeEventListener('mousemove', onMouseMove)
    document.body.removeEventListener('mouseup', onMouseUp)
}

    /*------------------------------------*/

function translate(el, x, y) {
    el.style.transform = `translate(${x}px, ${y}px)`
}

function drawLine(x1, x2, y1, y2, x3 ,x4, y3, y4) {
    context.clearRect(0, 0, width, height)
    context.beginPath()
    // из центра квадрата
    context.moveTo(x1 + size / 2, y1 + size / 2)
    // в центр другого квадрата
    context.lineTo(x2 + size / 2, y2 + size / 2)
    context.lineTo(x3 + size / 2, y3 + size / 2)
    context.lineTo(x4 + size / 2, y4 + size / 2)
    context.closePath()
    context.stroke()
    context.fill()
}
 })
</script>

<style>

</style>