<template>
  <html>
    <div id="appmain" class="lg:m-0 lg:pl-324px">
      <link
        href="https://unpkg.com/boxicons@2.0.7/css/boxicons.min.css"
        rel="stylesheet"
      />
      <Nav />
      <main class="bg-black w-full xl:ml-4">
        <Home :developmentMode="false" />
        <About :siteData="siteData" :tools="tools" />
        <!-- <Services /> -->
        <Works />
        <Contact />
      </main>
    </div>
  </html>
</template>

<script>
import gql from "graphql-tag";
const SITE_DATA_QUERY = gql`
  query MyQuery {
    siteData(where: { siteDataSlug: "sitedata" }) {
      aboutMe
      profileImage {
        url
      }
      resumeLink {
        url
      }
      developmentMode
    }
  }
`;

const ALL_TOOLS_QUERY = gql`
  query MyQuery {
    tools {
      name
      image {
        url
      }
      id
    }
  }
`;
export default {
  data() {
    return {
      siteData: {
        profileImage: {
          url: "https://firebasestorage.googleapis.com/v0/b/portfolios-aaca9.appspot.com/o/valneboh.jpeg?alt=media&token=08f837aa-5a17-4a0e-8c19-b37580db1352",
        },
        aboutMe:
          "Francis Val-Neboh - copywriter, paid traffic and customer acquisition expert - has been helping businesses grow by harnessing digital marketing platforms, and strategies using trainings and live workshops since 2014. He is the Founder, CEO at Kunyite Digital- a digital marketing and customer acquisition agency founded in 2019. His mission is to help 10,000 businesses STAND OUT and DOMINATE in their industries by leveraging the arsenal the internet provides.",
        resumeLink: {
          url: "https://firebasestorage.googleapis.com/v0/b/portfolios-aaca9.appspot.com/o/francis-resume.pdf?alt=media&token=ac50d101-3e57-41d7-a417-037ac2037813",
        },
      },
      tools: [
        {
          id: "1",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Ftypescript.svg?alt=media&token=ff0f82c1-0572-486c-9705-f0ab25cab518",
          },
          name: "TypeScript",
        },
        {
          id: "2",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fjavascript.svg?alt=media&token=4518d626-1639-4783-891f-214c5f5764ac",
          },
          name: "JavaScript",
        },
        {
          id: "3",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fsolidity2.png?alt=media&token=9a12b94f-5fc3-4bc2-aa8a-45318f52f112",
          },
          name: "Solidity",
        },
        {
          id: "4",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fpython.svg?alt=media&token=3f3bae3c-f251-4274-b4e9-ec7fe4a84ea3",
          },
          name: "Python",
        },
        {
          id: "5",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fflutter.png?alt=media&token=2633bdca-a8e2-4afd-b10f-6af5db70b351",
          },
          name: "Flutter",
        },
        {
          id: "6",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Freact.svg?alt=media&token=7bb627fa-b731-4c01-8cbb-c618ac130e61",
          },
          name: "React",
        },
        {
          id: "7",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fphp.svg?alt=media&token=8b1f3613-8d0c-46a9-9073-d668c3b3eb81",
          },
          name: "PHP",
        },
        {
          id: "8",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Ffirebase.svg?alt=media&token=efda7666-0db4-487a-b207-79fd2776b3df",
          },
          name: "Firebase",
        },
        {
          id: "9",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fgithub.svg?alt=media&token=88d0e8d7-807d-433f-b21a-19a5a5f8f31c",
          },
          name: "Github",
        },
        {
          id: "10",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2Fjson.svg?alt=media&token=8d32626a-36fa-40e7-9d04-56db8ed0aac5",
          },
          name: "REST API",
        },
        {
          id: "11",
          image: {
            url: "https://firebasestorage.googleapis.com/v0/b/paul-portfolio-6aec1.appspot.com/o/upload%2Ftools%2FSocket-io.svg?alt=media&token=8683e23d-3efe-4480-b41b-266b0cf2be63",
          },
          name: "Socket.IO",
        },
      ],
      error: null,
    };
  },
  apollo: {
    siteData: {
      query: SITE_DATA_QUERY,
      prefetch: true,
      error(error) {
        this.error = JSON.stringify(error.message);
      },
    },
    tools: {
      query: ALL_TOOLS_QUERY,
      prefetch: true,
      error(error) {
        this.error = JSON.stringify(error.message);
      },
    },
  },
};
</script>

html{ scroll-behavior: smooth; }
