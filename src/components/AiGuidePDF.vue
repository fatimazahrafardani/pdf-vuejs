<template>
    <div class="pdf-generator">
      <button @click="generatePDF" class="download-btn">Download AI Guide PDF</button>
      
      <div id="pdfContent" class="pdf-content">
        <h1>Complete Guide to AI Tools and Influencers</h1>
        
        <section>
          <h2>Top AI Influencers to Follow</h2>
          <ul>
            <li>Andrew Ng - @AndrewYNg</li>
            <li>Yann LeCun - @ylecun</li>
            <li>Fei-Fei Li - @drfeifei</li>
            <li>Sam Altman - @sama</li>
            <li>Demis Hassabis - @demishassabis</li>
          </ul>
        </section>
  
        <section>
          <h2>Free AI Tools for Everyone</h2>
          
          <h3>Content Creation</h3>
          <ul>
            <li>ChatGPT - Text generation and conversations</li>
            <li>Copy.ai - Free tier for content writing</li>
            <li>Canva AI - Image and design creation</li>
            <li>Bing Image Creator - Free image generation</li>
          </ul>
  
          <h3>Image Editing</h3>
          <ul>
            <li>Remove.bg - Background removal</li>
            <li>Pixlr - Online photo editor with AI features</li>
            <li>Deep Image - AI image upscaling</li>
          </ul>
  
          <h3>Audio & Video</h3>
          <ul>
            <li>Descript - Free video editing with AI</li>
            <li>Murf.ai - Text-to-speech (free tier)</li>
            <li>Kapwing - Online video editor with AI</li>
          </ul>
  
          <h3>Productivity</h3>
          <ul>
            <li>Notion AI - Note-taking and organization</li>
            <li>Grammarly - Writing assistance</li>
            <li>Otter.ai - Meeting transcription (free tier)</li>
          </ul>
        </section>
  
        <section>
          <h2>AI Learning Resources</h2>
          <ul>
            <li>Google AI - ai.google</li>
            <li>Fast.ai - Practical Deep Learning</li>
            <li>Elements of AI - Free online course</li>
            <li>MIT OpenCourseWare - AI courses</li>
            <li>Coursera - AI specializations</li>
          </ul>
        </section>
  
        <section>
          <h2>AI Communities</h2>
          <ul>
            <li>Hugging Face - AI community and models</li>
            <li>AI Discord servers</li>
            <li>Reddit r/artificial</li>
            <li>GitHub AI projects</li>
            <li>Kaggle - AI competitions</li>
          </ul>
        </section>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { jsPDF } from 'jspdf';
  import html2canvas from 'html2canvas';
  
  const generatePDF = async () => {
    const content = document.getElementById('pdfContent');
    if (!content) return;
  
    try {
      const canvas = await html2canvas(content);
      const imgData = canvas.toDataURL('image/png');
      
      const pdf = new jsPDF({
        orientation: 'portrait',
        unit: 'mm',
        format: 'a4'
      });
  
      const imgProps = pdf.getImageProperties(imgData);
      const pdfWidth = pdf.internal.pageSize.getWidth();
      const pdfHeight = (imgProps.height * pdfWidth) / imgProps.width;
      
      pdf.addImage(imgData, 'PNG', 0, 0, pdfWidth, pdfHeight);
      pdf.save('ai-guide.pdf');
    } catch (error) {
      console.error('Error generating PDF:', error);
    }
  };
  </script>
  
  <style scoped>
  .pdf-generator {
    max-width: 800px;
    margin: 2rem auto;
    padding: 2rem;
  }
  
  .download-btn {
    background-color: #d4af37;
    color: white;
    padding: 1rem 2rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1.1rem;
    margin-bottom: 2rem;
    transition: background-color 0.3s ease;
  }
  
  .download-btn:hover {
    background-color: #b39030;
  }
  
  .pdf-content {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  h1 {
    color: #333;
    font-size: 2rem;
    margin-bottom: 2rem;
    text-align: center;
  }
  
  h2 {
    color: #d4af37;
    font-size: 1.5rem;
    margin: 2rem 0 1rem;
  }
  
  h3 {
    color: #666;
    font-size: 1.2rem;
    margin: 1.5rem 0 0.5rem;
  }
  
  ul {
    list-style-type: none;
    padding-left: 0;
  }
  
  li {
    margin: 0.5rem 0;
    padding-left: 1.5rem;
    position: relative;
  }
  
  li::before {
    content: "•";
    color: #d4af37;
    position: absolute;
    left: 0;
  }
  
  section {
    margin-bottom: 2rem;
  }
  </style>