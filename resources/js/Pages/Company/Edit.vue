<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import SectionContainer from "@/Components/SectionContainer.vue";
import InputError from "@/Components/InputError.vue";
import { Link, useForm } from "@inertiajs/vue3";
import { vMaska } from "maska";

const props = defineProps({
    company: Object,
});

const form = useForm({
    name: props.company.name,
    cnpj: props.company.cnpj,
    phone: props.company.phone,
    address: props.company.address,
    address_number: props.company.address_number,
    address_complement: props.company.address_complement,
    neighborhood: props.company.neighborhood,
    zip_code: props.company.zip_code,
    city: props.company.city,
    state: props.company.state,
    email: props.company.email,
    logo: props.company.logo,
    pix_key: props.company.pix_key,
});

const submit = () => {
    form.put(route("company.update", props.company), form);
};
</script>

<template>
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Editar Empresa: {{ company.name }}
            </h2>
        </template>
        <SectionContainer>
            <form @submit.prevent="submit">
                <div class="grid grid-cols-2 gap-3">
                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Nome</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Nome da empresa"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.name"
                        />

                        <InputError class="mt-2" :message="form.errors.name" />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Cnpj</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.cnpj"
                            v-maska
                            data-maska="[
                              '##.###.###/####-##'
                            ]"
                        />
                        <InputError class="mt-2" :message="form.errors.cnpj" />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Email</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.email"
                        />
                        <InputError class="mt-2" :message="form.errors.email" />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Telefone</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.phone"
                            v-maska
                            data-maska="[
                              '(##) #####-####',
                              '(##) ####-####'
                            ]"
                        />
                        <InputError class="mt-2" :message="form.errors.phone" />
                    </label>
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <div class="flex gap-3">
                        <label class="form-control w-full">
                            <div class="label">
                                <span class="label-text">Endereço</span>
                            </div>
                            <input
                                type="text"
                                placeholder="Type here"
                                class="input input-bordered bg-inherit w-full"
                                v-model="form.address"
                            />
                            <InputError
                                class="mt-2"
                                :message="form.errors.address"
                            />
                        </label>

                        <label class="form-control w-24">
                            <div class="label">
                                <span class="label-text">Nº</span>
                            </div>
                            <input
                                type="text"
                                placeholder="Type here"
                                class="input input-bordered bg-inherit w-24"
                                v-model="form.address_number"
                                v-maska
                                data-maska="######"
                            />
                            <InputError
                                class="mt-2"
                                :message="form.errors.address_number"
                            />
                        </label>
                    </div>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Complemento</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.address_complement"
                        />
                    </label>
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Bairro</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.neighborhood"
                        />
                        <InputError
                            class="mt-2"
                            :message="form.errors.neighborhood"
                        />
                        <InputError
                            class="mt-2"
                            :message="form.errors.neighborhood"
                        />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">CEP</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.zip_code"
                            v-maska
                            data-maska="#####-###"
                        />
                        <InputError
                            class="mt-2"
                            :message="form.errors.zip_code"
                        />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Cidade</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.city"
                        />
                        <InputError class="mt-2" :message="form.errors.city" />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Estado</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.state"
                        />
                        <InputError class="mt-2" :message="form.errors.state" />
                    </label>
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Chave Pix</span>
                        </div>
                        <input
                            type="text"
                            placeholder="Type here"
                            class="input input-bordered bg-inherit w-full"
                            v-model="form.pix_key"
                        />
                    </label>

                    <label class="form-control w-full">
                        <div class="label">
                            <span class="label-text">Logo</span>
                        </div>

                        <input
                            type="file"
                            class="file-input w-full bg-inherit"
                            @change="form.logo = $event.target.files[0]"
                        />

                        <InputError class="mt-2" :message="form.errors.logo" />
                    </label>
                </div>

                <div class="flex items-center justify-between mt-4 gap-6">
                    <button
                        class="btn btn-success"
                        :class="{ 'opacity-25': form.processing }"
                        :disabled="form.processing"
                        type="submit"
                    >
                        Editar
                    </button>
                    <Link
                        :href="route('company.index')"
                        class="btn btn-error text-sm text-gray-600 hover:text-gray-900"
                    >
                        Cancelar
                    </Link>
                </div>
            </form>
        </SectionContainer>
    </AuthenticatedLayout>
</template>