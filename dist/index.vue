<style src="./style.css"></style>
<template src="./template.html"></template>

<script>
    export default {
        props: {
            label: String,
            inline: Boolean,
            required: Boolean,
            width: [String, Number],
            position: {
                type: String,
                default: 'left'
            },
            align: {
                type: String,
                default: 'right'
            }
        },
        computed: {
            style() {
                return {
                    width: `${this.width}px`
                }
            },
            clazz() {
                return {
                    'ui-field--inline': this.inline,
                    'ui-field--horizontal': this.position === 'top'
                }
            },
            labelClass() {
                let align = this.align.split('-')

                if(!align.includes('left') && !align.includes('right')) {
                    align.push('right')
                }
                
                return {
                    'ui-field__label': true,
                    'ui-field__label--required': this.required,
                    'ui-field__label--top': align.includes('top'),
                    'ui-field__label--left': align.includes('left'),
                    'ui-field__label--right': align.includes('right'),
                    'ui-field__label--bottom': align.includes('bottom')
                }
            }
        }
    }
</script>