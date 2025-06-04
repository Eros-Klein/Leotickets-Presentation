<template>
  <div class="roadmap-container" :class="{ 'in-slider': inSlider }">
    <h2 v-if="title" class="roadmap-title">{{ title }}</h2>
    
    <div class="roadmap-wrapper" ref="roadmapWrapper">
      <div class="nav-arrow nav-arrow-left">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="15,18 9,12 15,6"></polyline>
        </svg>
      </div>
      
      <div class="nav-arrow nav-arrow-right">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="9,6 15,12 9,18"></polyline>
        </svg>
      </div>
      
      <div class="roadmap-timeline">
        <div class="timeline-start">{{ formatDate(timeRange.start) }}</div>
        <div class="timeline-end">{{ formatDate(timeRange.end) }}</div>
        <div class="timeline-line"></div>
        
        <div 
          v-for="(item, index) in roadmapData" 
          :key="index"
          class="roadmap-item"
          :class="{ 
            'completed': item.status === 'completed',
            'current': item.status === 'current',
            'upcoming': item.status === 'upcoming'
          }"
          :style="{ left: calculatePosition(item.time) + '%' }"
        >
          <div class="roadmap-marker">
            <div class="marker-dot"></div>
            <div class="marker-pulse" v-if="item.status === 'current'"></div>
          </div>
          
          <div class="connecting-bar"></div>
          
          <div class="roadmap-content">
            <div class="content-card">
              <h3 class="item-title">{{ item.title }}</h3>
              <p class="item-description" v-if="item.description">{{ item.description }}</p>
              <div class="item-meta">
                <span class="item-date">{{ formatDate(item.time) }}</span>
                <span class="item-status" :class="item.status">{{ item.status }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Roadmap',
  props: {
    data: {
      type: Array,
      required: true,
      default: () => []
    },
    timeRange: {
      type: Object,
      default: () => ({
        start: new Date(Date.now() - 365 * 24 * 60 * 60 * 1000),
        end: new Date(Date.now() + 365 * 24 * 60 * 60 * 1000)
      })
    },
    title: {
      type: String,
      default: ''
    },
    inSlider: {
      type: Boolean,
      default: false
    }
  },

  computed: {
    roadmapData() {
      return this.data.map(item => ({
        ...item,
        time: new Date(item.time)
      })).sort((a, b) => a.time - b.time);
    }
  },

  methods: {
    calculatePosition(itemTime) {
      const startTime = this.timeRange.start.getTime();
      const endTime = this.timeRange.end.getTime();
      const itemTimeMs = itemTime.getTime();
      
      // Calculate percentage position along timeline
      const percentage = ((itemTimeMs - startTime) / (endTime - startTime)) * 100;
      
      // Ensure position is within bounds
      return Math.max(0, Math.min(100, percentage));
    },
    
    formatDate(date) {
      return date.toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'short',
        day: 'numeric'
      });
    }
  }
}
</script>

<style scoped>
.roadmap-container {
  width: 100%;
  min-width: 300px;
  padding: 2rem;
  font-family: 'Inter', sans-serif;
  overflow: hidden;
}

/* For use within sliders/carousels */
.roadmap-container.in-slider {
  padding: 1rem;
  min-width: 280px;
  max-width: 100%;
}

.roadmap-title {
  text-align: center;
  margin-bottom: 3rem;
  font-size: 2rem;
  font-weight: 600;
  color: #581c87;
}

.roadmap-wrapper {
  position: relative;
  overflow-x: auto;
  overflow-y: visible;
  padding: 4rem 2rem;
  min-height: 300px;
}

.roadmap-timeline {
  position: relative;
  width: 100%;
  height: 200px;
}

.timeline-start {
  position: absolute;
  top: calc(50% + 15px);
  left: 0;
  font-size: 0.75rem;
  color: #8b5cf6;
  font-weight: 500;
}

.timeline-end {
  position: absolute;
  top: calc(50% + 15px);
  right: 0;
  font-size: 0.75rem;
  color: #8b5cf6;
  font-weight: 500;
}

.timeline-line {
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #ddd6fe 0%, #8b5cf6 50%, #ddd6fe 100%);
  border-radius: 2px;
  transform: translateY(-50%);
}

.roadmap-item {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 10;
}

.roadmap-marker {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 20px;
  height: 20px;
  transform: translate(-50%, -50%);
  z-index: 15;
}

.marker-dot {
  position: absolute;
  top: 0;
  left: 0;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  transition: all 0.3s ease;
  border: 3px solid #fff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.marker-pulse {
  position: absolute;
  top: 0;
  left: 0;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% {
    box-shadow: 0 0 0 0 rgba(139, 92, 246, 0.7);
  }
  70% {
    box-shadow: 0 0 0 10px rgba(139, 92, 246, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(139, 92, 246, 0);
  }
}

.roadmap-item.completed .marker-dot {
  background-color: #10b981;
  border-color: #10b981;
}

.roadmap-item.current .marker-dot {
  background-color: #8b5cf6;
  border-color: #8b5cf6;
  transform: scale(1.2);
}

.roadmap-item.upcoming .marker-dot {
  background-color: #6b7280;
  border-color: #6b7280;
}

.connecting-bar {
  position: absolute;
  top: calc(50% + 10px);
  left: 50%;
  width: 2px;
  height: 40px;
  background-color: #ddd6fe;
  transform: translateX(-50%);
  z-index: 5;
  transition: background-color 0.3s ease;
}

/* Connecting bar for items above the timeline */
.roadmap-item:nth-child(even) .connecting-bar {
  top: auto;
  bottom: calc(50% + 10px);
  height: 40px;
}

.roadmap-item.completed .connecting-bar {
  background-color: #10b981;
}

.roadmap-item.current .connecting-bar {
  background-color: #8b5cf6;
}

.roadmap-item.upcoming .connecting-bar {
  background-color: #6b7280;
}

.roadmap-content {
  position: absolute;
  top: calc(50% + 50px);
  left: 50%;
  transform: translateX(-50%);
  width: clamp(120px, 20vw, 160px);
  max-width: 160px;
}

.content-card {
  background: linear-gradient(135deg, #faf5ff 0%, #f3e8ff 100%);
  border-radius: 6px;
  padding: 0.5rem;
  box-shadow: 0 1px 4px rgba(139, 92, 246, 0.15);
  border: 1px solid #d8b4fe;
  transition: all 0.3s ease;
  max-width: 100%;
  width: 100%;
  box-sizing: border-box;
}

.content-card:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 15px rgba(139, 92, 246, 0.25);
  border-color: #c084fc;
}

.item-title {
  font-size: 0.8rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
  color: #581c87;
  line-height: 1.1;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.item-description {
  font-size: 0.7rem;
  color: #7c3aed;
  margin-bottom: 0.5rem;
  line-height: 1.2;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
}

.item-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.item-date {
  font-size: 0.65rem;
  color: #a855f7;
  font-weight: 500;
}

.item-status {
  font-size: 0.6rem;
  padding: 0.15rem 0.4rem;
  border-radius: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.item-status.completed {
  background-color: #d1fae5;
  color: #065f46;
}

.item-status.current {
  background-color: #e9d5ff;
  color: #6b21a8;
}

.item-status.upcoming {
  background-color: #f3f4f6;
  color: #374151;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .roadmap-container {
    padding: 0.5rem;
  }
  
  .roadmap-wrapper {
    padding: 2rem 0.5rem;
  }
  
  .timeline-start,
  .timeline-end {
    font-size: 0.7rem;
  }
  
  .roadmap-content {
    width: clamp(100px, 25vw, 140px);
    max-width: 140px;
  }
  
  .connecting-bar {
    height: 30px;
  }
  
  .roadmap-item:nth-child(even) .connecting-bar {
    height: 30px;
  }
  
  .roadmap-content {
    top: calc(50% + 40px);
  }
  
  .roadmap-item:nth-child(even) .roadmap-content {
    bottom: calc(50% + 40px);
  }
  
  .content-card {
    padding: 0.4rem;
  }
  
  .item-title {
    font-size: 0.75rem;
  }
  
  .item-description {
    font-size: 0.65rem;
  }
  
  .item-date {
    font-size: 0.6rem;
  }
  
  .item-status {
    font-size: 0.55rem;
    padding: 0.1rem 0.3rem;
  }
}

/* Extra small screens */
@media (max-width: 480px) {
  .timeline-start,
  .timeline-end {
    font-size: 0.65rem;
  }
  
  .roadmap-content {
    width: clamp(80px, 30vw, 120px);
    max-width: 120px;
  }
  
  .connecting-bar {
    height: 25px;
  }
  
  .roadmap-item:nth-child(even) .connecting-bar {
    height: 25px;
  }
  
  .roadmap-content {
    top: calc(50% + 35px);
  }
  
  .roadmap-item:nth-child(even) .roadmap-content {
    bottom: calc(50% + 35px);
  }
  
  .content-card {
    padding: 0.3rem;
  }
  
  .item-title {
    font-size: 0.7rem;
  }
  
  .item-description {
    font-size: 0.6rem;
    -webkit-line-clamp: 1;
  }
  
  .item-date {
    font-size: 0.55rem;
  }
  
  .item-status {
    font-size: 0.5rem;
    padding: 0.1rem 0.25rem;
  }
}

/* Handle overlapping items */
.roadmap-item:nth-child(even) .roadmap-content {
  top: auto;
  bottom: calc(50% + 50px);
}

/* Direction indicators */
.nav-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 30px;
  height: 30px;
  color: #8b5cf6;
  z-index: 25;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0.7;
}

.nav-arrow-left {
  left: 10px;
}

.nav-arrow-right {
  right: 10px;
}

/* Responsive indicators */
@media (max-width: 768px) {
  .nav-arrow {
    width: 24px;
    height: 24px;
  }
}

@media (max-width: 480px) {
  .nav-arrow {
    width: 20px;
    height: 20px;
  }
}
</style>
