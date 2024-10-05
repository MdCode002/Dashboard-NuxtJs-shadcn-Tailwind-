<script setup>
import {
AlertDialog,
AlertDialogAction,
AlertDialogCancel,
AlertDialogContent,
AlertDialogFooter,
AlertDialogHeader,
AlertDialogTitle,
AlertDialogTrigger
} from '@/components/ui/alert-dialog';
import { Input } from '@/components/ui/input';

const { loading, open } = useHelpers();

const createNewProduct = async () => {
  try {
    loading.value = true

    // my call
  } catch (error) {
    throw new Error(error)
  } finally {
    loading.value = false;
    open.value = false;
  }
}
</script>

<template>
  <AlertDialog :open="open">
    <AlertDialogTrigger>
      <Button @click="open = true">Add a new product</Button>
    </AlertDialogTrigger>
    <AlertDialogContent>
      <AlertDialogHeader>
        <AlertDialogTitle>Create a new product</AlertDialogTitle>
        <Input placeholder="My product name" />
      </AlertDialogHeader>
      <AlertDialogFooter>
        <AlertDialogCancel @click="open = false">Cancel</AlertDialogCancel>
        <AlertDialogAction @click="createNewProduct()">Create</AlertDialogAction>
      </AlertDialogFooter>
    </AlertDialogContent>
  </AlertDialog>
</template>