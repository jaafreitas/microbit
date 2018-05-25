# Mostra Interativa
Projetos demonstrados durante a Campus Party 2018 no Espaço Educação do Futuro na área da [Rede Brasileira de Aprendizagem Criativa](http://aprendizagemcriativa.org/).


## microbit-#RoboPiscaNeoPixel
```javascript
let item: neopixel.Strip = null
let index = 0
index = 0
item = neopixel.create(DigitalPin.P0, 16, NeoPixelMode.RGB)
// O pino P11 deve ser ligado ao GND
basic.forever(() => {
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P12, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(500)
    // Olho direito
    pins.digitalWritePin(DigitalPin.P12, 1)
    basic.pause(500)
    // Olho esquerdo
    pins.digitalWritePin(DigitalPin.P13, 1)
    basic.pause(500)
    // Vermelho
    pins.digitalWritePin(DigitalPin.P14, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P14, 0)
    // Azul
    pins.digitalWritePin(DigitalPin.P15, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P15, 0)
    // Verde
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P16, 0)
})
basic.forever(() => {
    basic.showString("Estudio Hacker")
})
basic.forever(() => {
    for (let i = 0; i < 10; i++) {
        for (let index2 = 0; index2 <= 2; index2++) {
            item.range(index2, 1).showColor(neopixel.colors(NeoPixelColors.Red))
            item.shift(1)
            item.range(index2, 1).showColor(neopixel.colors(NeoPixelColors.Orange))
            item.shift(1)
            item.range(index2, 1).showColor(neopixel.colors(NeoPixelColors.Yellow))
            basic.pause(100)
        }
    }
    for (let i = 0; i < 10; i++) {
        for (let index3 = 0; index3 <= 2; index3++) {
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Red))
            item.shift(1)
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Orange))
            item.shift(1)
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Yellow))
            item.shift(1)
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Green))
            item.shift(1)
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Blue))
            item.shift(1)
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Violet))
            item.shift(1)
            item.range(index3, 1).showColor(neopixel.colors(NeoPixelColors.Purple))
            basic.pause(100)
        }
    }
    for (let i = 0; i < 20; i++) {
        for (let index4 = 0; index4 <= 2; index4++) {
            item.range(index4, 1).showColor(neopixel.colors(NeoPixelColors.Blue))
            item.shift(1)
            basic.pause(30)
        }
    }
    for (let i = 0; i < 30; i++) {
        for (let index5 = 0; index5 <= 2; index5++) {
            item.range(index5, 1).showColor(neopixel.colors(NeoPixelColors.Purple))
            item.shift(1)
            basic.pause(20)
        }
    }
})
```

## microbit-Bússola
```javascript
let degrees = 0
basic.forever(() => {
    degrees = input.compassHeading()
    if (degrees < 45 || degrees > 315) {
        basic.showString("N")
    } else if (degrees < 135) {
        basic.showString("L")
    } else if (degrees < 225) {
        basic.showString("S")
    } else {
        basic.showString("O")
    }
})
```

## microbit-Dado
```javascript
let numero = 0
input.onGesture(Gesture.Shake, () => {
    basic.showIcon(IconNames.SmallDiamond)
    radio.sendNumber(0)
    basic.pause(1000)
    numero = 1 + Math.random(6)
    basic.showNumber(numero)
    radio.sendNumber(numero)
})
radio.onDataPacketReceived( ({ receivedNumber }) =>  {
    if (receivedNumber == 0) {
        basic.showIcon(IconNames.SmallDiamond)
    } else {
        basic.showNumber(receivedNumber)
    }
})
radio.setGroup(101)
```

## microbit-Gráfico-Luminosidade
```javascript
basic.forever(() => {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
```

## microbit-Jokenpô
```javascript
let tool = 0
input.onGesture(Gesture.Shake, () => {
    tool = Math.random(3)
    basic.clearScreen()
    basic.pause(1000)
    if (tool == 0) {
        basic.showLeds(`
            # # # # #
            # . . . #
            # . . . #
            # . . . #
            # # # # #
            `)
    } else if (tool == 1) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else {
        basic.showLeds(`
            # # . . #
            # # . # .
            . . # . .
            # # . # .
            # # . . #
            `)
    }
})
tool = 0
```

## microbit-Letreiro-Estúdio-Hacker
```javascript
input.onButtonPressed(Button.A, () => {
    basic.showString("Campus")
    basic.pause(2000)
})
input.onButtonPressed(Button.B, () => {
    basic.showString("Party")
    basic.pause(2000)
})
basic.forever(() => {
    basic.showString("Estudio Hacker")
    basic.pause(5000)
})
```

## microbit-MusicBox
```javascript
input.onGesture(Gesture.Shake, () => {
    music.beginMelody(music.builtInMelody(Melodies.Nyan), MelodyOptions.OnceInBackground)
})
input.onGesture(Gesture.TiltLeft, () => {
    music.beginMelody(music.builtInMelody(Melodies.Wedding), MelodyOptions.OnceInBackground)
})
input.onGesture(Gesture.TiltRight, () => {
    music.beginMelody(music.builtInMelody(Melodies.Blues), MelodyOptions.OnceInBackground)
})
input.onGesture(Gesture.LogoUp, () => {
    music.beginMelody(music.builtInMelody(Melodies.Funk), MelodyOptions.OnceInBackground)
})
input.onGesture(Gesture.ScreenDown, () => {
    music.beginMelody(music.builtInMelody(Melodies.Chase), MelodyOptions.OnceInBackground)
})
input.onGesture(Gesture.LogoDown, () => {
    music.beginMelody(music.builtInMelody(Melodies.Baddy), MelodyOptions.OnceInBackground)
})
input.onButtonPressed(Button.A, () => {
    music.beginMelody(music.builtInMelody(Melodies.Birthday), MelodyOptions.OnceInBackground)
})
input.onButtonPressed(Button.B, () => {
    music.beginMelody(music.builtInMelody(Melodies.Entertainer), MelodyOptions.OnceInBackground)
})
input.onButtonPressed(Button.AB, () => {
    music.beginMelody(music.builtInMelody(Melodies.Funeral), MelodyOptions.OnceInBackground)
})
basic.forever(() => {
    basic.showLeds(`
        . # # # #
        . # . . #
        . # . # #
        # # . # #
        # # . . .
        `)
})
```

## microbit-Pisca-Leds
```javascript
basic.forever(() => {
    led.toggle(Math.random(5), Math.random(5))
})
```

## microbit-Termômetro
```javascript
basic.forever(() => {
    basic.showNumber(input.temperature())
    basic.clearScreen()
    basic.pause(5000)
})
```

## microbit-Tilts
```javascript
input.onGesture(Gesture.LogoUp, () => {
    basic.showString("U")
})
input.onGesture(Gesture.TiltLeft, () => {
    basic.showString("L")
})
input.onGesture(Gesture.TiltRight, () => {
    basic.showString("R")
})
input.onGesture(Gesture.LogoDown, () => {
    basic.showString("D")
})
```
