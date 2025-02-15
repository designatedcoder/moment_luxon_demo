<script setup>
    import moment from 'moment';
    import { DateTime } from 'luxon';

    defineProps({
        users: {
            type: Array,
        },
    });

    const momentTime = ((item) => {
        return moment(item).format('MMMM D, YYYY')
    });

    const luxonTime = ((item) => {
        // return DateTime.fromISO(item).toFormat('MMMM d, yyyy')
        return DateTime.fromISO(item).setLocale('fr').toLocaleString();
    });
</script>

<template>
    <div class="min-h-screen">
        <div class="flex justify-around items-center min-h-screen">
            <table>
                <thead>
                    <tr class="text-green-600 text-2xl font-semibold">
                        Laravel
                    </tr>
                    <tr>
                        <th>name</th>
                        <th>created</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(user, index) in users" :key="index">
                        <td>{{ user.name }}</td>
                        <td class="pl-4">{{ user.created_format }}</td>
                    </tr>
                </tbody>
            </table>

            <table>
                <thead>
                    <tr class="text-red-600 text-2xl font-semibold">
                        Moment JS
                    </tr>
                    <tr>
                        <th>name</th>
                        <th>created</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(user, index) in users" :key="index">
                        <td>{{ user.name }}</td>
                        <td class="pl-4">{{ momentTime(user.created_at) }}</td>
                    </tr>
                </tbody>
            </table>

            <table>
                <thead>
                    <tr class="text-blue-600 text-2xl font-semibold">
                        Luxon
                    </tr>
                    <tr>
                        <th>name</th>
                        <th>created</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(user, index) in users" :key="index">
                        <td>{{ user.name }}</td>
                        <td class="pl-4">{{ luxonTime(user.created_at) }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
