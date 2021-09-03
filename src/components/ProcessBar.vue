<template>
    <div class="modal-wrap">
        <div class="modal">
            <div class="modal-header">
                <h1>{{title}}</h1>
            </div>

            <div class="modal-body">
                <div class="bar-container">
                    <span
                        :class="status.id <= currentStatusIndex ? '' : 'remaining'"
                        class="bar-data"
                        v-for="status in pettyCashStatuses"
                        :key="status.id"
                    >
                        <span
                            class="bar-circle"
                        >
                            <i>{{status.id}}</i>
                        </span>
                        <span class="bar-status">{{status.name}}</span>
                    </span>
                </div>

                <div class="bar-description-container">{{currentStatusDescription}}</div>
            </div>

            <div class="modal-footer">
                <!-- <button class="button">Omitir tour</button> -->
                <button class="button" @click="returnStatus">Anterior</button>
                <button class="button" @click="advanceStatus">Siguiente</button>
                <!-- <button class="button">Finalizar tour</button> -->
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ProcessBar',
        props: {
            title: {
                type: String,
                required: false,
                default: 'Proceso General de una Caja Chica'
            }
        },
        data() {
            return {
                currentStatusIndex: 1,
                pettyCashStatuses: [
                    {
                        id: 1,
                        name: 'Autorizada',
                        description: 'Cuando se asigna una caja chica y ya se hizo la validación presupuestal, se llega a este estatus.',
                    },
                    {
                        id: 2,
                        name: 'Activa',
                        description: 'Cuando se realiza el pago del fondeo inicial de la caja chica con el colaborador asignado llegamos a este estatus.',
                    },
                    {
                        id: 3,
                        name: 'Sin asignar',
                        description: 'Cuando el colaborador asignado ya no será responsable de la Caja chica.',
                    },
                    {
                        id: 4,
                        name: 'Inactiva',
                        description: 'Cuando una Caja chica activa, ha sido liberada del colaborador asignado y ya no se va a utilizar en ese momento.',
                    },
                    {
                        id: 5,
                        name: 'Solicitud de presupuesto',
                        description: 'Cuando se asigna la caja chica y al generar la solicitud de fondeo se comprueba que no existen recursos suficientes en el mes para realizar el pago del fondeo inicial.',
                    },
                    {
                        id: 6,
                        name: 'Rechazada',
                        description: 'Cuando no hubo presupuesto, o cuando no se puede realizar el pago del fondeo inicial.',
                    },
                    {
                        id: 7,
                        name: 'Cancelada',
                        description: 'Cuando se crea una Caja chica y se asigna, pero se marca como rechazada, pues se decide que no será utilizada antes de estar como “Activa” por primera vez.',
                    },
                ],
                pettyCashRequestStatuses: [],
                expenseTypeAdvanceStatuses: [],
                expenseTypeRemainingStatuses: [],
            };
        },
        methods: {
            returnStatus() {
                if (this.pettyCashStatuses.length > 0 && this.currentStatusIndex > 1) {
                    this.currentStatusIndex--;
                }
            },
            advanceStatus() {
                if (this.pettyCashStatuses.length > 0 && this.currentStatusIndex < this.pettyCashStatuses.length) {
                    this.currentStatusIndex++;
                }
            }
        },
        computed: {
            currentStatusDescription() {
                let pettyCashStatus = this.pettyCashStatuses.find(status => status.id === this.currentStatusIndex);
                return pettyCashStatus ? pettyCashStatus.description : '';
            }
        }
    }
</script>

<style lang="scss">
    @import '../sass/process_bar.scss';
</style>