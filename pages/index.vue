<template>
  <div class="container">
    <div
      v-for="(box, index) in arrangedBoxes"
      :key="index"
      :style="{
        width: (box.width - 10) + 'px',
        height: (box.height - 10) + 'px',
        top: box.top + 'px',
        left: box.left + 'px'
      }"
      class="box"
    >
      {{ box.content }}
      Top:  {{ box.top }}
      Height: {{ box.height }} 
      Width : {{ box.width }}
      total: {{ box.height + box.top }}
      left: {{ box.left }}
      left+ Width: {{ box.left + box.width }}

    
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      boxes: [
    {'height': 424, 'left': 0, 'top': 0, 'width': 600, 'content': 'box 1'},
    {'height': 530, 'left': 0, 'top': 0, 'width': 372, 'content': 'box 2'},
    {'height': 336, 'left': 0, 'top': 0, 'width': 250, 'content': 'box 3'},
    {'height': 300, 'left': 0, 'top': 0, 'width': 350, 'content': 'box 4'},
    {'height': 494, 'left': 0, 'top': 0, 'width': 371, 'content': 'box 6'},
    {'height': 300, 'left': 0, 'top': 0, 'width': 250, 'content': 'box 7'},
    {'height': 280, 'left': 0, 'top': 0, 'width': 350, 'content': 'box 8'},
    {'height': 385, 'left': 0, 'top': 0, 'width': 250, 'content': 'box 9'},
    {'height': 418, 'left': 0, 'top': 0, 'width': 418, 'content': 'box 10'},
    {'height': 100, 'left': 0, 'top': 0, 'width': 200, 'content': 'box 11'},
   // {'height': 48, 'left': 0, 'top': 0, 'width': 301, 'content': 'box 11'},




      ],
      containerWidth: 1000,
    };
  },
  computed: {
    arrangedBoxes() {
        let new_arrangement = [];
        let remaining_boxes = [...this.boxes];
        let previous_row_boxes = [];
        let row_number = 1;
        let lowestTopPlusHeightInRow = 0;  // Initialize lowest top + height tracker

        while (remaining_boxes.length > 0) {
            let current_row_boxes = [];
            let current_row_width = 0;
            lowestTopPlusHeightInRow = Infinity;  // Reset for each new row


        if (previous_row_boxes.length > 0) {
          for (let prev_box of previous_row_boxes) {
            let target_width = prev_box.width;
            let matching_boxes = this.findBoxes(remaining_boxes, target_width);
            if (matching_boxes.length > 0) {
              current_row_boxes.push(...matching_boxes);
              for (let box of matching_boxes) {
                let index = remaining_boxes.indexOf(box);
                if (index !== -1) remaining_boxes.splice(index, 1);
                current_row_width += box.width;
              }
            }
          }
        }

        if (current_row_boxes.length === 0 || current_row_width < this.containerWidth) {
          for (let box of remaining_boxes) {
            let widthExists = current_row_boxes.some(existingBox => existingBox.width === box.width);
            if (!widthExists && current_row_width + box.width <= this.containerWidth) {
              current_row_boxes.push(box);
              current_row_width += box.width;
            }
          }
        }

        if (current_row_boxes.length > 0) {
              let left_position = 0;
              for (let position = 0; position < current_row_boxes.length; position++) {
                let box = current_row_boxes[position];
                box.left = left_position;

                let highest_overlap = 0;
                if (previous_row_boxes.length > 0) {
                  for (let prev_box of previous_row_boxes) {
                    let overlaps = (prev_box.left + prev_box.width > box.left) && 
                                   (prev_box.left < box.left + box.width);
                    if (overlaps) {
                      highest_overlap = Math.max(highest_overlap, prev_box.top + prev_box.height);
                    }
                  }
                }

                // Compare highest_overlap with lowestTopPlusHeightInRow
                if(highest_overlap <= lowestTopPlusHeightInRow) {
                  box.top = highest_overlap;
                  lowestTopPlusHeightInRow = Math.min(lowestTopPlusHeightInRow, highest_overlap + box.height);  // Update tracker

                  new_arrangement.push({
                    content: `${row_number}.${position + 1} ${box.content}`,
                    top: box.top,
                    left: box.left,
                    width: box.width,
                    height: box.height,
                  });
                  left_position += box.width;
                }
              }

              for (let box of current_row_boxes) {
                let index = remaining_boxes.indexOf(box);
                if (index !== -1) remaining_boxes.splice(index, 1);
              }

              previous_row_boxes = [...current_row_boxes];
              row_number += 1;
            } else {
              break;
            }
        }

        return new_arrangement;
    },
  },
  methods: {
    findBoxes(remaining_boxes, target_width) {
      for (let box of remaining_boxes) {
        if (box.width === target_width) {
          return [box];
        }
      }
      for (let i = 0; i < remaining_boxes.length; i++) {
        for (let j = i + 1; j < remaining_boxes.length; j++) {
          let box1 = remaining_boxes[i];
          let box2 = remaining_boxes[j];
          if (box1.width + box2.width === target_width && box1.width !== box2.width) {
            return [box1, box2];
          }
        }
      }
      return [];
    },
  },
};

</script>

<style scoped>
.container {
  position: relative;
  width: 1000px;
}

.box {
  position: absolute;
  border: solid 1px red;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
