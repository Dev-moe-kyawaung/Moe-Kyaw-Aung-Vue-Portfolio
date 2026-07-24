# 🎨 Design Switching Guide

## How to Change Designs

### Option 1: Edit Home.vue
Simply replace the Home.vue content with any design from `src/components/designs/`

### Option 2: Use Design Components
```vue
<script setup>
// Import your preferred design
import DesignGlassmorphism from '@/components/designs/DesignGlassmorphism.vue'
// or
import DesignCyberpunk from '@/components/designs/DesignCyberpunk.vue'
// or
import DesignLuxury from '@/components/designs/DesignLuxury.vue'
// or
import DesignModernTech from '@/components/designs/DesignModernTech.vue'
// or
import DesignJapanese from '@/components/designs/DesignJapanese.vue'
</script>

