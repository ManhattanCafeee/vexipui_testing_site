<script setup lang="ts">
import {
  ArrowRightFromBracket,
  ChartPie,
  City,
  CommentDotsR,
  EnvelopesBulk,
  Gear,
  IdBadgeR,
  User,
} from '@vexip-ui/icons'

import { Alert, datePickerProps, type MenuOptions } from 'vexip-ui'
import 'vexip-ui/css/index.css'
import Form from './views/Form.vue'
import Button from './views/Button.vue'
import Input from './views/Input.vue'
import { ref, Ref } from 'vue'
const user = {
  name: 'null',
  email: 'manhattancaf33@gmail.com',
}


const actions = [
  {
    label: 'profile',
    icon: IdBadgeR,
    name: '个人资料',
  },
  {
    label: 'message',
    icon: CommentDotsR,
    name: '你的消息',
  },
  {
    label: 'settings',
    icon: Gear,
    name: '帐号设置',
    divided: true,
  },
  {
    label: 'signOut',
    name: '退出登录',
    icon: ArrowRightFromBracket,
  },
]

const menus: MenuOptions[] = [
  {
    label: '1',
    name: '菜单 1',
    icon: EnvelopesBulk,
    children: [
      { label: '1-1', name: '子菜单 1' },
      { label: '1-2', name: '子菜单 2' },
      { label: '1-3', name: '子菜单 3' },
    ],
  },
  {
    label: '2',
    name: '菜单 2',
    icon: City,
    disabled: true,
  },
  {
    label: '3',
    name: '菜单 3',
    icon: ChartPie,
  },
  {
    label: '4',
    name: '菜单 4',
    icon: User,
  },
]
const currentMenu = ref('')
function handleUserAction(label: string) {
  console.info(label)
}
function handleMenuSelect(label: string) {
  console.info('Selected menu:', label)
  alert(`go f yourself!`)
  currentMenu.value = label
}

function changeColor() {
  alert('color changed')
}
</script>

<template>
  <Layout logo="https://www.vexipui.com/vexip-ui.svg" sign-name="Vexip UI" :user="user" :actions="actions"
    :menus="menus" :avatar-circle="true" color="blue" copyright="manhatancafee all right reserved" :fit-window="true"
    :footer="true" @user-action="handleUserAction" @menu-select="handleMenuSelect" @color-change="changeColor">
    <template #main>
      <div>
        <Alert type="info" closable>
          You have selected menu: {{ currentMenu }}
        </Alert>
      </div>
      <div v-if="!currentMenu">
        <h2 style="text-align: center; "> Please select a menu item </h2>
      </div>
      <div v-if="currentMenu === '1-1'">
        <Form class="form_1" />
        <div class="form-button-container">
          <Button type="info" class="button_1">
            submit
          </Button>
        </div>
        <div class="input">
          <Input />
        </div>
      </div>


    </template>
  </Layout>
</template>


<style scoped>
.vxp-layout {
  height: 100vh;
  width: 100vw;
}

.form-button-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}



#main {
  display: flex;
  flex-direction: column;
  gap: 3%;
  justify-content: center;
  align-items: center;
}
</style>
<style>
body {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: flex-start;
}

#app {
  display: flex;
  flex-direction: row;
  padding: 0;
  justify-content: flex-start;
  ;
}

.input {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2%;
}
</style>