<script setup lang="ts">
import { EditorContent } from '@tiptap/vue-3'

import { EditorCommand } from '@entities/editor-command'
import { useTiptapEditor } from '@entities/use-tiptap-editor'

const { documentId } = defineProps<{ documentId: string }>()

const { editor } = useTiptapEditor(documentId)
</script>

<template>
  <div
    v-if="editor"
    class="relative w-full grow rounded-lg border bg-card p-5 pt-20 text-card-foreground shadow-sm 2xl:w-9/12 2xl:grow-0"
  >
    <EditorCommand :editor="editor" />
    <EditorContent :editor="editor" />
  </div>
</template>

<style>
.tiptap {
  height: 65dvh;

  overflow-y: scroll;

  outline: none;

  padding-top: 16px;
}

.collaboration-cursor__caret {
  border-left: 1px solid #0d0d0d;
  border-right: 1px solid #0d0d0d;
  margin-left: -1px;
  margin-right: -1px;
  pointer-events: none;
  position: relative;
  word-break: normal;
}

.collaboration-cursor__label {
  font-style: normal;
  font-weight: 600;
  left: -1px;
  line-height: normal;
  position: absolute;
  user-select: none;
  white-space: nowrap;
  font-size: 14px;
  color: #fff;
  top: -1.4em;
  border-radius: 6px;
  border-bottom-left-radius: 0;
  padding: 2px 6px;
  pointer-events: none;
}
</style>
