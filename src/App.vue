<template>
  <div id="app">
    <div class="flex-none bg-gray-800 w-64">
      <div class="text-white p-3 mb-2 border-b border-gray-700 font-medium text-base tracking-wide">
        Layers
        <button class="close-icon p-2 focus:outline-none focus:shadow-none float-right">
          <icon name="x" color="CapeCod" size="12"></icon>
        </button>
      </div>
      <DraggableTree class="tree3" :data="data" draggable="draggable" cross-tree="cross-tree">
        <div
          class="flex items-center rounded-sm p-1 mx-2 hover:bg-gray-700 mb-1"
          slot-scope="{data, store}"
        >
          <template v-if="!data.isDragPlaceHolder">
            <button
              class="flex focus:outline-none focus:shadow-none"
              @click.prevent="store.toggleOpen(data)"
            >
              <icon
                :name="data.open ? 'triangle-down' : 'triangle-right'"
                size="12"
                class="mr-1"
                :class="{ 'opacity-0': !data.children.length }"
              ></icon>
            </button>

            <icon :name="items[data.text].icon || 'div'" size="12" color="CapeCod" class="mr-1"></icon>

            <span class="text-xs text-gray-200">
              {{
              items[data.text].text || data.text
              }}
            </span>
          </template>
        </div>
      </DraggableTree>
    </div>
  </div>
</template>

<script>
import Icon from "./components/Icon.vue";
import { DraggableTree } from "vue-draggable-nested-tree/dist/vue-draggable-nested-tree.js";

export default {
  name: "app",
  components: {
    Icon,
    DraggableTree
  },
  data() {
    return {
      data: [
        {
          text: "body",
          className: "p-10 xl:p-20",
          draggable: false,
          children: [
            {
              text: "div",
              className: "",
              draggable: true,
              children: [
                {
                  text: "h1",
                  className: "text-3xl font-bold",
                  description: "Welcome back, Ignas!",
                  droppable: false
                },
                {
                  text: "p",
                  className: "text-lg text-gray-500 tracking-wide mb-10",
                  description:
                    "You have learned 80% of the course. Keep it up and improve your results!",
                  droppable: false
                },
                {
                  text: "h1",
                  className: "text-xl font-semibold mb-5",
                  description: "Your next classes",
                  droppable: false
                }
              ]
            },
            {
              text: "div",
              className: "flex -mx-4",
              draggable: true,
              children: [
                {
                  text: "div",
                  className: "flex-1 flex bg-blue-500 p-6 rounded-lg mx-4",
                  children: [
                    {
                      text: "div",
                      className:
                        "bg-blue-400 h-12 w-12 flex items-center justify-center rounded-lg mr-4",
                      children: [
                        {
                          text: "h1",
                          className: "text-lg font-bold text-white",
                          description: "B2",
                          droppable: false
                        }
                      ]
                    },
                    {
                      text: "div",
                      className: "",
                      children: [
                        {
                          text: "p",
                          className: "text-white opacity-75 font-medium",
                          description: "Business English",
                          droppable: false
                        },
                        {
                          text: "h1",
                          className: "text-xl text-white font-bold",
                          description: "Grammar",
                          droppable: false
                        }
                      ]
                    }
                  ]
                },
                {
                  text: "div",
                  className: "flex-1 flex bg-blue-500 p-6 rounded-lg mx-4",
                  children: [
                    {
                      text: "div",
                      className:
                        "bg-blue-400 h-12 w-12 flex items-center justify-center rounded-lg mr-4",
                      children: [
                        {
                          text: "h1",
                          className: "text-lg font-bold text-white",
                          description: "B2",
                          droppable: false
                        }
                      ]
                    },
                    {
                      text: "div",
                      className: "",
                      children: [
                        {
                          text: "p",
                          className: "text-white opacity-75 font-medium",
                          description: "Business Spanish",
                          droppable: false
                        },
                        {
                          text: "h1",
                          className: "text-xl text-white font-bold",
                          description: "Vocabulary",
                          droppable: false
                        }
                      ]
                    }
                  ]
                },
                {
                  text: "div",
                  className: "flex-1 flex bg-blue-500 p-6 rounded-lg mx-4",
                  items: [
                    {
                      text: "div",
                      className:
                        "bg-blue-400 h-12 w-12 flex items-center justify-center rounded-lg mr-4",
                      children: [
                        {
                          text: "h1",
                          className: "text-lg font-bold text-white",
                          description: "B2"
                        }
                      ]
                    },
                    {
                      text: "div",
                      className: "",
                      children: [
                        {
                          text: "p",
                          className: "text-white opacity-75 font-medium",
                          description: "Business French",
                          droppable: false
                        },
                        {
                          text: "h1",
                          className: "text-xl text-white font-bold",
                          description: "Vocabulary",
                          droppable: false
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ]
        }
      ],
      items: {
        body: {
          icon: "layout",
          name: "Body"
        },
        div: {
          icon: "div",
          name: "Div block"
        },
        h1: {
          icon: "heading",
          name: "Heading"
        },
        p: {
          icon: "paragraph",
          name: "Paragraph"
        },
        button: {
          icon: "pointer",
          name: "Button"
        }
      }
    };
  }
};
</script>
