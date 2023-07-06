

<!DOCTYPE html>
<html lang="en-GB"
      dir="ltr"
      class="">
<head>
    <title>01. Create Mesh - Geom... | VLUTE Wiki</title>

    <!-- Meta -->
    <meta charset="utf-8">
    <meta name="robots" content="nofollow" />
    <meta name="viewport" content="width=device-width">
    <meta name="token" content="C0r52hiNx0iJBj8e9JrdQiWozxtcDwEk1ta7EWbv">
    <meta name="base-url" content="http://huongdan.fit.vlute.edu.vn">
    <meta name="theme-color" content="#206ea7"/>

    <!-- Social Cards Meta -->
    <meta property="og:title" content="01. Create Mesh - Geom... | VLUTE Wiki">
    <meta property="og:url" content="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/01-create-mesh-geometric-objects">
        <meta property="og:description" content="Tạo lưới (Mesh) từ mảng NumPy và cách tạo các đối tượng hình học nguyên thủy như hình cầu, mũi tên,...">

    <!-- Styles and Fonts -->
    <link rel="stylesheet" href="http://huongdan.fit.vlute.edu.vn/dist/styles.css?version=v23.01.1">
    <link rel="stylesheet" media="print" href="http://huongdan.fit.vlute.edu.vn/dist/print-styles.css?version=v23.01.1">

    <!-- Icons -->
    <link rel="icon" type="image/png" sizes="256x256" href="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/BqSlogo-1.png">
    <link rel="icon" type="image/png" sizes="180x180" href="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/5sPlogo-1.png">
    <link rel="apple-touch-icon" sizes="180x180" href="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/5sPlogo-1.png">
    <link rel="icon" type="image/png" sizes="128x128" href="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/Dkologo-1.png">
    <link rel="icon" type="image/png" sizes="64x64" href="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/aXklogo-1.png">
    <link rel="icon" type="image/png" sizes="32x32" href="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/bvalogo-1.png">

    
    <!-- Custom Styles & Head Content -->
    <style>
    :root {
        --color-primary: #206ea7;
        --color-primary-light: rgba(32,110,167,0.15);
        --color-link: #206ea7;
        --color-bookshelf: #a94747;
        --color-book: #077b70;
        --color-chapter: #af4d0d;
        --color-page: #206ea7;
        --color-page-draft: #7e50b1;
    }
</style>
    <!-- Start: custom user content -->
<style nonce="lBkCpI7kVa2AOtkMAxsWkAP6">
.page-content h1,
.page-content h2, 
.page-content h3, 
.page-content h4, 
.page-content h5, 
.page-content h6, 
.page-content pre {
    clear: left;
    font-weight: 500;
}
  
.page-content h1,
.page-content h2, 
.page-content h3, 
.page-content h4, 
.page-content h5, 
.page-content pre {
	color: var(--color-primary);
}
  
table {
    width: 100%;
}
  
td {
    text-align: center;
}
  
.page-content .CodeMirror-sizer, .page-content .CodeMirror-scroll {
	/* background: #eeffcc; */
}
  
.content-wrap code {
    display: inline;
    padding: 1px 3px;
    white-space: pre-wrap;
    line-height: 1.2em;
    color: #e74c3c;
    white-space: normal;
    font-weight: bold;
}
  
.page-content img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
}
</style>
<!-- End: custom user content -->

    
    <!-- Translations for JS -->
    </head>
<body
          class=" tri-layout ">

        <a class="px-m py-s skip-to-content-link print-hidden" href="#main-content">Skip to main content</a>    <div component="notification"
     option:notification:type="success"
     option:notification:auto-hide="true"
     option:notification:show="false"
     style="display: none;"
     class="notification pos"
     role="alert">
    <svg class="svg-icon" data-icon="check-circle" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
</svg> <span></span><div class="dismiss"><svg class="svg-icon" data-icon="close" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg></div>
</div>

<div component="notification"
     option:notification:type="warning"
     option:notification:auto-hide="false"
     option:notification:show="false"
     style="display: none;"
     class="notification warning"
     role="alert">
    <svg class="svg-icon" data-icon="info" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M11 17h2v-6h-2v6zm1-15C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zM11 9h2V7h-2v2z"/>
</svg> <span></span><div class="dismiss"><svg class="svg-icon" data-icon="close" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg></div>
</div>

<div component="notification"
     option:notification:type="error"
     option:notification:auto-hide="false"
     option:notification:show="false"
     style="display: none;"
     class="notification neg"
     role="alert">
    <svg class="svg-icon" data-icon="danger" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.73 3H8.27L3 8.27v7.46L8.27 21h7.46L21 15.73V8.27L15.73 3zM12 17.3c-.72 0-1.3-.58-1.3-1.3 0-.72.58-1.3 1.3-1.3.72 0 1.3.58 1.3 1.3 0 .72-.58 1.3-1.3 1.3zm1-4.3h-2V7h2v6z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg> <span></span><div class="dismiss"><svg class="svg-icon" data-icon="close" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg></div>
</div>    <header id="header" component="header-mobile-toggle" class="primary-background">
    <div class="grid mx-l">

        <div>
            <a href="http://huongdan.fit.vlute.edu.vn" data-shortcut="home_view" class="logo">
                                    <img class="logo-image" src="http://huongdan.fit.vlute.edu.vn/uploads/images/system/2023-03/logo-1.png" alt="Logo">
                                                    <span class="logo-text">VLUTE Wiki</span>
                            </a>
            <button type="button"
                    refs="header-mobile-toggle@toggle"
                    title="Expand Header Menu"
                    aria-expanded="false"
                    class="mobile-menu-toggle hide-over-l"><svg class="svg-icon" data-icon="more" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M12 8c1.1 0 2-.9 2-2s-.9-2-2-2-2 .9-2 2 .9 2 2 2zm0 2c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm0 6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/>
</svg></button>
        </div>

        <div class="flex-container-column items-center justify-center hide-under-l">
                        <form component="global-search" action="http://huongdan.fit.vlute.edu.vn/search" method="GET" class="search-box" role="search" tabindex="0">
                <button id="header-search-box-button"
                        refs="global-search@button"
                        type="submit"
                        aria-label="Search"
                        tabindex="-1"><svg class="svg-icon" data-icon="search" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg></button>
                <input id="header-search-box-input"
                       refs="global-search@input"
                       type="text"
                       name="term"
                       data-shortcut="global_search"
                       autocomplete="off"
                       aria-label="Search" placeholder="Search"
                       value="">
                <div refs="global-search@suggestions" class="global-search-suggestions card">
                    <div refs="global-search@loading" class="text-center px-m global-search-loading"><div class="loading-container">
    <div></div>
    <div></div>
    <div></div>
    </div></div>
                    <div refs="global-search@suggestion-results" class="px-m"></div>
                    <button class="text-button card-footer-link" type="submit">View All</button>
                </div>
            </form>
                    </div>

        <nav refs="header-mobile-toggle@menu" class="header-links">
            <div class="links text-center">
                                    <a class="hide-over-l" href="http://huongdan.fit.vlute.edu.vn/search"><svg class="svg-icon" data-icon="search" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg>Search</a>
                    
                    
                                        
                                    
                                                        <a href="http://huongdan.fit.vlute.edu.vn/login"><svg class="svg-icon" data-icon="login" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M21 3.01H3c-1.1 0-2 .9-2 2V9h2V4.99h18v14.03H3V15H1v4.01c0 1.1.9 1.98 2 1.98h18c1.1 0 2-.88 2-1.98v-14c0-1.11-.9-2-2-2zM11 16l4-4-4-4v3H1v2h10v3z"/>
</svg>Log in</a>
                            </div>
                    </nav>

    </div>
</header>

    <div id="content" components="tri-layout" class="block">
        
    <div class="tri-layout-mobile-tabs print-hidden">
        <div class="grid half no-break no-gap">
            <button type="button"
                    refs="tri-layout@tab"
                    data-tab="info"
                    aria-label="Tab: Show Secondary Information"
                    class="tri-layout-mobile-tab px-m py-m text-link">
                Info
            </button>
            <button type="button"
                    refs="tri-layout@tab"
                    data-tab="content"
                    aria-label="Tab: Show Primary Content"
                    aria-selected="true"
                    class="tri-layout-mobile-tab px-m py-m text-link active">
                Content
            </button>
        </div>
    </div>

    <div refs="tri-layout@container" class="tri-layout-container"  >

        <div class="tri-layout-left print-hidden" id="sidebar">
            <aside class="tri-layout-left-contents">
                
    
    
            <nav id="page-navigation" class="mb-xl" aria-label="Page Navigation">
            <h5>Page Navigation</h5>
            <div class="body">
                <div class="sidebar-page-nav menu">
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-m%E3%B4i-tr%E6%B0%E1%BB%9Dng-c%E3%A0i-%E4%91%E1%BA%B7t-v" class="text-limit-lines-1 block">Môi trường cài đặt VSCode (Python)</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-m%E3%B4i-tr%E6%B0%E1%BB%9Dng-c%E3%A0i-%E4%91%E1%BA%B7t-c" class="text-limit-lines-1 block">Môi trường cài đặt Colab Notebook</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-install-pyvista" class="text-limit-lines-1 block">install pyvista</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-thi%E1%BA%BFt-l%E1%BA%ADp-m%E3%B4i-tr%E6%B0%E1%BB%9Dng" class="text-limit-lines-1 block">Thiết lập môi trường</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h1">
                            <a href="#bkmrk-t%E1%BA%A1o-m%E1%BB%99t-l%E6%B0%E1%BB%9Bi-c%E3%B3-c%E1%BA%A5u-" class="text-limit-lines-1 block">Tạo một lưới có cấu trúc rõ ràng từ các mảng NumPy.</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-k%E1%BA%BFt-qu%E1%BA%A3%3A" class="text-limit-lines-1 block">Kết quả:</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h1">
                            <a href="#bkmrk-%E4%90%E1%BB%91i-t%E6%B0%E1%BB%A3ng-h%E3%ACnh-h%E1%BB%8Dc" class="text-limit-lines-1 block">Đối tượng hình học</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h2">
                            <a href="#bkmrk-m%E1%BB%99t-s%E1%BB%91-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng-h" class="text-limit-lines-1 block">Một số đối tượng hình học</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-hi%E1%BB%83n-th%E1%BB%8B-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng" class="text-limit-lines-1 block">Hiển thị đối tượng</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-k%E1%BA%BFt-qu%E1%BA%A3%3A-0" class="text-limit-lines-1 block">Kết quả:</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h1">
                            <a href="#bkmrk-%E4%90%E1%BB%91i-t%E6%B0%E1%BB%A3ng-h%E3%ACnh-h%E1%BB%8Dc-" class="text-limit-lines-1 block">Đối tượng hình học tham số</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-import-th%E6%B0-vi%E1%BB%87n" class="text-limit-lines-1 block">Import thư viện</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-kh%E1%BB%FFi-t%E1%BA%A1o-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng" class="text-limit-lines-1 block">Khởi tạo đối tượng</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-hi%E1%BB%83n-th%E1%BB%8B-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng-0" class="text-limit-lines-1 block">Hiển thị đối tượng</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-b%E3%A0i-t%E1%BA%ADp-4%3A-th%E1%BB%B1c-hi%E1%BB%87n-" class="text-limit-lines-1 block">Bài tập 4: Thực hiện khởi tạo và hiển thị đối tượng cho các Đối tượng hình học tham số phía trên (Gồ</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h1">
                            <a href="#bkmrk-pixel-art-of-alien-m" class="text-limit-lines-1 block">Pixel Art of ALIEN MONSTERS</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-import-th%E6%B0-vi%E1%BB%87n-0" class="text-limit-lines-1 block">Import thư viện</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-chuy%E1%BB%83n-pixel-th%E3%A0nh-m%E1%BA%A3" class="text-limit-lines-1 block">Chuyển pixel thành mảng</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-x%E3%A2y-d%E1%BB%B1ng-h%E3%A0m-draw-pixe" class="text-limit-lines-1 block">Xây dựng hàm draw pixels</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                            <li class="page-nav-item h3">
                            <a href="#bkmrk-hi%E1%BB%83n-th%E1%BB%8B-alien-monst" class="text-limit-lines-1 block">Hiển thị ALIEN MONSTERS</a>
                            <div class="link-background sidebar-page-nav-bullet"></div>
                        </li>
                                    </div>
            </div>
        </nav>
    
    <nav id="book-tree"
     class="book-tree mb-xl"
     aria-label="Book Navigation">

    <h5>Book Navigation</h5>

    <ul class="sidebar-page-list mt-xs menu entity-list">
                    <li class="list-item-book book">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d" class="book   entity-list-item" data-entity-type="book" data-entity-id="23">
    <span role="presentation" class="icon text-book"><svg class="svg-icon" data-icon="book" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M18 2H6c-1.1 0-2 .9-2 2v16c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zM6 4h5v8l-2.5-1.5L6 12V4z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">TH1345 - MÔ HÌNH HÓA HÌNH HỌC 3D</h4>
            
    </div>
</a>            </li>
        
                    <li class="list-item-page page ">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/chapter-1-chuyen-anh-sang-3d-su-dung-pifuhd" class="page   entity-list-item" data-entity-type="page" data-entity-id="72">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">Chapter 1: Chuyển ảnh sang 3D sử dụng PIFuHD</h4>
            
    </div>
</a>
                
            </li>
                    <li class="list-item-chapter chapter ">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/chapter/chapter-2-pyvista" class="chapter   entity-list-item" data-entity-type="chapter" data-entity-id="22">
    <span role="presentation" class="icon text-chapter"><svg class="svg-icon" data-icon="chapter" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M4 6H2v14c0 1.1.9 2 2 2h14v-2H4V6zm16-4H8c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-1 9H9V9h10v2zm-4 4H9v-2h6v2zm4-8H9V5h10v2z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">Chapter 2: PyVista</h4>
            
    </div>
</a>
                                    <div class="entity-list-item no-hover">
                        <span role="presentation" class="icon text-chapter"></span>
                        <div class="content">
                            <div component="chapter-contents" class="chapter-child-menu">
    <button type="button"
            refs="chapter-contents@toggle"
            aria-expanded="true"
            class="text-muted chapter-contents-toggle  open ">
        <svg class="svg-icon" data-icon="caret-right" role="presentation"  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M9.5 17.5l5-5-5-5z"/><path d="M0 0h24v24H0z" fill="none"/></svg> <svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg> <span>8 Pages</span>
    </button>
    <ul refs="chapter-contents@list"
        class="chapter-contents-list sub-menu inset-list  open "         style="display: block;"         role="menu">
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/01-create-mesh-geometric-objects" class="page  selected entity-list-item" data-entity-type="page" data-entity-id="100">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">01. Create Mesh - Geometric Objects</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/02-mesh-creation-platonic-solids-va-polydata" class="page   entity-list-item" data-entity-type="page" data-entity-id="111">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">02. Mesh Creation - Platonic Solids và PolyData</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/03-create-point-cloud-dam-may-diem" class="page   entity-list-item" data-entity-type="page" data-entity-id="174">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">03. Create Point Cloud - Đám mây điểm</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/04-filtering-mot-so-bo-loc" class="page   entity-list-item" data-entity-type="page" data-entity-id="190">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">04 Filtering - Một số bộ lọc</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/05-plotting-truc-quan-hoa" class="page   entity-list-item" data-entity-type="page" data-entity-id="191">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">05 Plotting - Trực quan hóa</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/06-luoi-phi-cau-truc-unstructuredgrid" class="page   entity-list-item" data-entity-type="page" data-entity-id="215">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">06. Lưới phi cấu trúc - UnstructuredGrid</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/07-lighting" class="page   entity-list-item" data-entity-type="page" data-entity-id="198">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">07. Lighting</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/08-danh-gia-chat-luong-mesh" class="page   entity-list-item" data-entity-type="page" data-entity-id="199">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">08. Đánh giá chất lượng mesh</h4>
            
    </div>
</a>            </li>
            </ul>
</div>                        </div>
                    </div>

                
            </li>
                    <li class="list-item-page page ">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/chapter-3-surface-subdivision" class="page   entity-list-item" data-entity-type="page" data-entity-id="179">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">Chapter 3: Surface Subdivision</h4>
            
    </div>
</a>
                
            </li>
                    <li class="list-item-page page ">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/chapter-4-bien-dang-luoi-3d" class="page   entity-list-item" data-entity-type="page" data-entity-id="185">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">Chapter 4: Biến dạng lưới 3D</h4>
            
    </div>
</a>
                
            </li>
                    <li class="list-item-chapter chapter ">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/chapter/chapter-5-ket-xuat-rendering" class="chapter   entity-list-item" data-entity-type="chapter" data-entity-id="27">
    <span role="presentation" class="icon text-chapter"><svg class="svg-icon" data-icon="chapter" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M4 6H2v14c0 1.1.9 2 2 2h14v-2H4V6zm16-4H8c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-1 9H9V9h10v2zm-4 4H9v-2h6v2zm4-8H9V5h10v2z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">Chapter 5: Kết xuất - Rendering</h4>
            
    </div>
</a>
                                    <div class="entity-list-item no-hover">
                        <span role="presentation" class="icon text-chapter"></span>
                        <div class="content">
                            <div component="chapter-contents" class="chapter-child-menu">
    <button type="button"
            refs="chapter-contents@toggle"
            aria-expanded="false"
            class="text-muted chapter-contents-toggle ">
        <svg class="svg-icon" data-icon="caret-right" role="presentation"  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M9.5 17.5l5-5-5-5z"/><path d="M0 0h24v24H0z" fill="none"/></svg> <svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg> <span>4 Pages</span>
    </button>
    <ul refs="chapter-contents@list"
        class="chapter-contents-list sub-menu inset-list "         role="menu">
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/01-ket-xuat-luoi-fit-mesh" class="page   entity-list-item" data-entity-type="page" data-entity-id="112">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">01. Kết xuất lưới - Fit Mesh</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/02-render-densepose-meshes" class="page   entity-list-item" data-entity-type="page" data-entity-id="113">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">02. Render DensePose Meshes</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/03-render-colored-pointclouds" class="page   entity-list-item" data-entity-type="page" data-entity-id="114">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">03. Render Colored Pointclouds</h4>
            
    </div>
</a>            </li>
                    <li class="list-item-page " role="presentation">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/04-camera-position-optimization-with-differentiable-rendering" class="page   entity-list-item" data-entity-type="page" data-entity-id="116">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">04. Camera Position Optimization with Differentiable Rendering</h4>
            
    </div>
</a>            </li>
            </ul>
</div>                        </div>
                    </div>

                
            </li>
                    <li class="list-item-page page ">
                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/chapter-6-on-tap" class="page   entity-list-item" data-entity-type="page" data-entity-id="217">
    <span role="presentation" class="icon text-page"><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
    <div class="content">
            <h4 class="entity-list-item-name break-text">Chapter 6: Ôn tập</h4>
            
    </div>
</a>
                
            </li>
            </ul>
</nav>            </aside>
        </div>

        <div class=" tri-layout-middle">
            <div id="main-content" class="tri-layout-middle-contents">
                
    <div class="mb-m print-hidden">
        <nav class="breadcrumbs text-center" aria-label="Breadcrumb">
    
    
            
        <a href="#" class="text-book icon-list-item outline-hover">
            <span><svg class="svg-icon" data-icon="books" role="presentation"  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M0 0h24v24H0z" fill="none"/><path d="M19.252 1.708H8.663a1.77 1.77 0 0 0-1.765 1.764v14.12c0 .97.794 1.764 1.765 1.764h10.59a1.77 1.77 0 0 0 1.764-1.765V3.472a1.77 1.77 0 0 0-1.765-1.764zM8.663 3.472h4.412v7.06L10.87 9.208l-2.206 1.324z"/><path d="M30.61 3.203h24v24h-24z" fill="none"/><path d="M2.966 6.61v14c0 1.1.9 2 2 2h14v-2h-14v-14z"/></svg></span>
            <span>Books</span>
        </a>
            
    
    
            
                
                                    <div class="dropdown-search" components="dropdown dropdown-search"
     option:dropdown-search:url="/search/entity/siblings?entity_type=book&entity_id=23"
     option:dropdown-search:local-search-selector=".entity-list-item"
>
    <div class="dropdown-search-toggle-breadcrumb" refs="dropdown@toggle"
         aria-haspopup="true" aria-expanded="false" tabindex="0">
        <div class="separator"><svg class="svg-icon" data-icon="chevron-right" role="presentation"  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/><path d="M0 0h24v24H0z" fill="none"/></svg></div>
    </div>
    <div refs="dropdown@menu" class="dropdown-search-dropdown card" role="menu">
        <div class="dropdown-search-search">
            <svg class="svg-icon" data-icon="search" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg>            <input refs="dropdown-search@searchInput"
                   aria-label="Search"
                   autocomplete="off"
                   placeholder="Search"
                   type="text">
        </div>
        <div refs="dropdown-search@loading">
            <div class="loading-container">
    <div></div>
    <div></div>
    <div></div>
    </div>        </div>
        <div refs="dropdown-search@listContainer" class="dropdown-search-list px-m" tabindex="-1"></div>
    </div>
</div>                        <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d" class="text-book icon-list-item outline-hover">
                <span><svg class="svg-icon" data-icon="book" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M18 2H6c-1.1 0-2 .9-2 2v16c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zM6 4h5v8l-2.5-1.5L6 12V4z"/>
</svg></span>
                <span>
                    TH1345 - MÔ HÌNH HÓA H...
                </span>
            </a>
                            
                
                                    <div class="dropdown-search" components="dropdown dropdown-search"
     option:dropdown-search:url="/search/entity/siblings?entity_type=chapter&entity_id=22"
     option:dropdown-search:local-search-selector=".entity-list-item"
>
    <div class="dropdown-search-toggle-breadcrumb" refs="dropdown@toggle"
         aria-haspopup="true" aria-expanded="false" tabindex="0">
        <div class="separator"><svg class="svg-icon" data-icon="chevron-right" role="presentation"  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/><path d="M0 0h24v24H0z" fill="none"/></svg></div>
    </div>
    <div refs="dropdown@menu" class="dropdown-search-dropdown card" role="menu">
        <div class="dropdown-search-search">
            <svg class="svg-icon" data-icon="search" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg>            <input refs="dropdown-search@searchInput"
                   aria-label="Search"
                   autocomplete="off"
                   placeholder="Search"
                   type="text">
        </div>
        <div refs="dropdown-search@loading">
            <div class="loading-container">
    <div></div>
    <div></div>
    <div></div>
    </div>        </div>
        <div refs="dropdown-search@listContainer" class="dropdown-search-list px-m" tabindex="-1"></div>
    </div>
</div>                        <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/chapter/chapter-2-pyvista" class="text-chapter icon-list-item outline-hover">
                <span><svg class="svg-icon" data-icon="chapter" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M4 6H2v14c0 1.1.9 2 2 2h14v-2H4V6zm16-4H8c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-1 9H9V9h10v2zm-4 4H9v-2h6v2zm4-8H9V5h10v2z"/>
</svg></span>
                <span>
                    Chapter 2: PyVista
                </span>
            </a>
                            
                
                                    <div class="dropdown-search" components="dropdown dropdown-search"
     option:dropdown-search:url="/search/entity/siblings?entity_type=page&entity_id=100"
     option:dropdown-search:local-search-selector=".entity-list-item"
>
    <div class="dropdown-search-toggle-breadcrumb" refs="dropdown@toggle"
         aria-haspopup="true" aria-expanded="false" tabindex="0">
        <div class="separator"><svg class="svg-icon" data-icon="chevron-right" role="presentation"  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/><path d="M0 0h24v24H0z" fill="none"/></svg></div>
    </div>
    <div refs="dropdown@menu" class="dropdown-search-dropdown card" role="menu">
        <div class="dropdown-search-search">
            <svg class="svg-icon" data-icon="search" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg>            <input refs="dropdown-search@searchInput"
                   aria-label="Search"
                   autocomplete="off"
                   placeholder="Search"
                   type="text">
        </div>
        <div refs="dropdown-search@loading">
            <div class="loading-container">
    <div></div>
    <div></div>
    <div></div>
    </div>        </div>
        <div refs="dropdown-search@listContainer" class="dropdown-search-list px-m" tabindex="-1"></div>
    </div>
</div>                        <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/01-create-mesh-geometric-objects" class="text-page icon-list-item outline-hover">
                <span><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
                <span>
                    01. Create Mesh - Geom...
                </span>
            </a>
                    </nav>    </div>

    <main class="content-wrap card">
        <div component="page-display"
             option:page-display:page-id="100"
             class="page-content clearfix">
            <div dir="auto">

    <h1 class="break-text" id="bkmrk-page-title">01. Create Mesh - Geometric Objects</h1>

    <div style="clear:left;"></div>

            <p id="bkmrk-t%E1%BA%A1o-l%E6%B0%E1%BB%9Bi-%28mesh%29-t%E1%BB%AB-">Tạo lưới (Mesh) từ mảng NumPy và cách tạo các đối tượng hình học nguyên thủy như hình cầu, mũi tên, hình khối, hình elip.</p>
<h6 id="bkmrk-m%E3%B4i-tr%E6%B0%E1%BB%9Dng-c%E3%A0i-%E4%91%E1%BA%B7t-v"><strong>Môi trường cài đặt VSCode (Python)</strong></h6>
<hr id="bkmrk-">
<h6 id="bkmrk-m%E3%B4i-tr%E6%B0%E1%BB%9Dng-c%E3%A0i-%E4%91%E1%BA%B7t-c"><strong>Môi trường cài đặt Colab Notebook</strong></h6>
<h6 id="bkmrk-install-pyvista">install pyvista</h6>
<pre id="bkmrk-%21apt-get-install--qq"><code>!apt-get install -qq xvfb libgl1-mesa-glx
!pip install pyvista -qq
</code></pre>
<h6 id="bkmrk-thi%E1%BA%BFt-l%E1%BA%ADp-m%E3%B4i-tr%E6%B0%E1%BB%9Dng">Thiết lập môi trường</h6>
<pre id="bkmrk-import-pyvista-pyvis"><code>import pyvista
pyvista.global_theme.jupyter_backend = 'static'
pyvista.global_theme.notebook = True
pyvista.start_xvfb()
</code></pre>
<hr id="bkmrk--0">
<h4 id="bkmrk-t%E1%BA%A1o-m%E1%BB%99t-l%E6%B0%E1%BB%9Bi-c%E3%B3-c%E1%BA%A5u-"><strong>Tạo một lưới có cấu trúc rõ ràng từ các mảng NumPy.</strong></h4>
<pre id="bkmrk-import-numpy-as-np-i"><code class="language-python">import numpy as np

import pyvista as pv

ni, nj, nk = 4, 5, 6
si, sj, sk = 20, 10, 1

xcorn = np.arange(0, (ni + 1) * si, si)
xcorn = np.repeat(xcorn, 2)
xcorn = xcorn[1:-1]
xcorn = np.tile(xcorn, 4 * nj * nk)

ycorn = np.arange(0, (nj + 1) * sj, sj)
ycorn = np.repeat(ycorn, 2)
ycorn = ycorn[1:-1]
ycorn = np.tile(ycorn, (2 * ni, 2 * nk))
ycorn = np.transpose(ycorn)
ycorn = ycorn.flatten()

zcorn = np.arange(0, (nk + 1) * sk, sk)
zcorn = np.repeat(zcorn, 2)
zcorn = zcorn[1:-1]
zcorn = np.repeat(zcorn, (4 * ni * nj))

corners = np.stack((xcorn, ycorn, zcorn))
corners = corners.transpose()

if pv._vtk.VTK9:
    dims = np.asarray((ni, nj, nk)) + 1
    grid = pv.ExplicitStructuredGrid(dims, corners)
    grid = grid.compute_connectivity()
    grid.plot(show_edges=True)
</code></pre>
<h6 id="bkmrk-k%E1%BA%BFt-qu%E1%BA%A3%3A">Kết quả:</h6>
<p id="bkmrk--1"><a href="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/image-1682229883545.png"><img src="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/scaled-1680-/image-1682229883545.png" alt=""></a></p>
<hr id="bkmrk--2">
<p id="bkmrk-b%E3%A0i-t%E1%BA%ADp-1%3A-th%E1%BB%B1c-hi%E1%BB%87n-">Bài tập 1: Thực hiện tùy chỉnh lưới với số dòng 4, số cột 3, số lớp 7</p>
<hr id="bkmrk--3">
<h4 id="bkmrk-%E4%90%E1%BB%91i-t%E6%B0%E1%BB%A3ng-h%E3%ACnh-h%E1%BB%8Dc">Đối tượng hình học</h4>
<h5 id="bkmrk-m%E1%BB%99t-s%E1%BB%91-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng-h">Một số đối tượng hình học</h5>
<pre id="bkmrk-cyl-%3D-pv.cylinder%28%29-"><code class="language-python">cyl = pv.Cylinder()
arrow = pv.Arrow()
sphere = pv.Sphere()
plane = pv.Plane()
line = pv.Line()
box = pv.Box()
cone = pv.Cone()
poly = pv.Polygon()
disc = pv.Disc()
</code></pre>
<h6 id="bkmrk-hi%E1%BB%83n-th%E1%BB%8B-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng">Hiển thị đối tượng</h6>
<pre id="bkmrk-p-%3D-pv.plotter%28shape"><code class="language-python">p = pv.Plotter(shape=(1, 1))
p.add_mesh(cyl)
p.show()
</code></pre>
<h6 id="bkmrk-k%E1%BA%BFt-qu%E1%BA%A3%3A-0">Kết quả:</h6>
<p id="bkmrk--4"><a href="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/image-1682230265120.png"><img src="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/scaled-1680-/image-1682230265120.png" alt=""></a></p>
<hr id="bkmrk--5">
<p id="bkmrk-b%E3%A0i-t%E1%BA%ADp-2%3A-th%E1%BB%B1c-hi%E1%BB%87n-">Bài tập 2: Thực hiện hiển thị tất cả đối tượng hình học sử dụng hàm subplot</p>
<p id="bkmrk--6"><a href="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/image-1682230442134.png"><img src="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/scaled-1680-/image-1682230442134.png" alt=""></a></p>
<p id="bkmrk-b%E3%A0i-t%E1%BA%ADp-3%3A-th%E1%BB%B1c-hi%E1%BB%87n-">Bài tập 3: Thực hiện hiển thị tất cả đối tượng hình học với thuộc tính color và hiển thị đường viền như ảnh</p>
<p id="bkmrk--7"><a href="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/image-1682230592766.png"><img src="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/scaled-1680-/image-1682230592766.png" alt=""></a></p>
<hr id="bkmrk--8">
<h4 id="bkmrk-%E4%90%E1%BB%91i-t%E6%B0%E1%BB%A3ng-h%E3%ACnh-h%E1%BB%8Dc-"><strong>Đối tượng hình học tham số</strong></h4>
<ol id="bkmrk-supertoroid-parametr">
<li>Supertoroid</li>
<li>Parametric Ellipsoid</li>
<li>Partial Parametric Ellipsoid</li>
<li>Pseudosphere</li>
<li>Bohemian Dome</li>
<li>Bour</li>
<li>Boy’s Surface (Boy)</li>
<li>Catalan Minimal</li>
<li>Conic Spiral</li>
<li>Cross Cap</li>
<li>Dini</li>
<li>Enneper</li>
<li>Figure-8 Klein</li>
<li>Henneberg</li>
<li>Klein</li>
<li>Kuen</li>
<li>Mobius</li>
<li>Plucker Conoid</li>
<li>Random Hills</li>
<li>Roman</li>
<li>Super Ellipsoid</li>
<li>Torus</li>
<li>Extruded Half Arc</li>
</ol>
<h6 id="bkmrk-import-th%E6%B0-vi%E1%BB%87n">Import thư viện</h6>
<pre id="bkmrk-from-math-import-pi-"><code>from math import pi
import pyvista as pv
</code></pre>
<h6 id="bkmrk-kh%E1%BB%FFi-t%E1%BA%A1o-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng">Khởi tạo đối tượng</h6>
<pre id="bkmrk-supertoroid-%3D-pv.par"><code>supertoroid = pv.ParametricSuperToroid(n1=0.5)
</code></pre>
<h6 id="bkmrk-hi%E1%BB%83n-th%E1%BB%8B-%E4%91%E1%BB%91i-t%E6%B0%E1%BB%A3ng-0">Hiển thị đối tượng</h6>
<pre id="bkmrk-supertoroid.plot%28col"><code>supertoroid.plot(color="tan", smooth_shading=True)
</code></pre>
<p id="bkmrk--9"><a href="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/image-1682300711200.png"><img src="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/scaled-1680-/image-1682300711200.png" alt=""></a></p>
<hr id="bkmrk--10">
<h6 id="bkmrk-b%E3%A0i-t%E1%BA%ADp-4%3A-th%E1%BB%B1c-hi%E1%BB%87n-"><strong>Bài tập 4: Thực hiện khởi tạo và hiển thị đối tượng cho các Đối tượng hình học tham số phía trên (Gồm 24 đối tượng) với color là cyan.</strong></h6>
<p id="bkmrk-c%E3%BA-ph%E3%A1p%3A-pv.parametric">Cú pháp: pv.Parametric<strong>TenDoiTuongHinhHoc</strong>(thuộc tính nếu có)</p>
<p id="bkmrk-m%E1%BB%99t-s%E1%BB%91-thu%E1%BB%99c-t%E3%ADnh-%E4%91%E1%BB%91"><strong>Một số thuộc tính đối tượng</strong></p>
<ol id="bkmrk-parametricellipsoid%28">
<li>ParametricEllipsoid(10, 5, 5)</li>
<li>Partial Parametric Ellipsoid</li>
</ol>
<pre id="bkmrk-cpos-%3D-%5B-%2821.9930%2C-2"><code>cpos = [
    (21.9930, 21.1810, -30.3780),
    (-1.1640, -1.3098, -0.1061),
    (0.8498, -0.2515, 0.4631),
]

</code></pre>
<ul id="bkmrk-parametric-ellipsoid">
<li>Parametric Ellipsoid(10, 5, 5, max_v=pi / 2)</li>
<li>Hiển thị đối tượng có thêm thuộc tính smooth_shading=True và cpos=cpos</li>
</ul>
<ol start="3" id="bkmrk-pseudosphere%3A-smooth">
<li>Pseudosphere: smooth_shading=True</li>
<li>Enneper cpos = "yz"</li>
<li>Super Ellipsoid(n1=0.1, n2=2)</li>
<li>Circular Arc</li>
</ol>
<pre id="bkmrk-pointa-%3D-%5B-1%2C-0%2C-0%5D-"><code>pointa = [-1, 0, 0]
pointb = [0, 1, 0]
center = [0, 0, 0]
resolution = 100

arc = pv.CircularArc(pointa, pointb, center, resolution)

pl = pv.Plotter()
pl.add_mesh(arc, color='k', line_width=4)
pl.show_bounds()
pl.view_xy()
pl.show()
</code></pre>
<ol start="7" id="bkmrk-extruded-half-arc">
<li>Extruded Half Arc</li>
</ol>
<pre id="bkmrk-pointa-%3D-%5B-1%2C-0%2C-0%5D--0"><code>pointa = [-1, 0, 0]
pointb = [1, 0, 0]
center = [0, 0, 0]
resolution = 100

arc = pv.CircularArc(pointa, pointb, center, resolution)
poly = arc.extrude([0, 0, 1])
poly.plot(color="tan", cpos='iso', show_edges=True)
</code></pre>
<hr id="bkmrk--11">
<h4 id="bkmrk-pixel-art-of-alien-m"><strong>Pixel Art of ALIEN MONSTERS</strong></h4>
<h6 id="bkmrk-import-th%E6%B0-vi%E1%BB%87n-0">Import thư viện</h6>
<pre id="bkmrk-import-pyvista-as-pv"><code>import pyvista as pv
from pyvista.demos import logo
</code></pre>
<h6 id="bkmrk-chuy%E1%BB%83n-pixel-th%E3%A0nh-m%E1%BA%A3">Chuyển pixel thành mảng</h6>
<pre id="bkmrk-alien_str-%3D-%22%22%22-%25-%25-"><code>alien_str = """
    %         %
      %     %
    % % % % % %
  % %   % %   % %
% % % % % % % % % %
%   % % % % % %   %
%   %         %   %
%   % %     % %   %
      %     %
    %         %
"""

alien = []
for line in alien_str.splitlines()[1:]:  # skip first linebreak
    if not line:
        continue
    if len(line) &lt; 20:
        line += (20 - len(line)) * ' '
    alien.append([line[i : i + 2] == '% ' for i in range(0, len(line), 2)])
</code></pre>
<h6 id="bkmrk-x%E3%A2y-d%E1%BB%B1ng-h%E3%A0m-draw-pixe">Xây dựng hàm draw pixels</h6>
<pre id="bkmrk-def-draw_pixels%28plot"><code>def draw_pixels(plotter, pixels, center, color):
    bounds = [
        center[0] - 1.0,
        center[0] + 1.0,
        center[1] - 1.0,
        center[1] + 1.0,
        -10.0,
        +10.0,
    ]
    for rows in pixels:
        for pixel in rows:
            if pixel:
                box = pv.Box(bounds=bounds)
                plotter.add_mesh(box, color=color)
            bounds[0] += 2.0
            bounds[1] += 2.0
        bounds[0] = center[0] - 1.0
        bounds[1] = center[0] + 1.0
        bounds[2] += -2.0
        bounds[3] += -2.0
    return plotter
</code></pre>
<h6 id="bkmrk-hi%E1%BB%83n-th%E1%BB%8B-alien-monst">Hiển thị ALIEN MONSTERS</h6>
<pre id="bkmrk-%23-display-monsters-p"><code># Display MONSTERS
p = pv.Plotter()
p = draw_pixels(p, alien, [-22.0, 22.0], "green")
p = draw_pixels(p, alien, [0.0, 22.0], "green")
p = draw_pixels(p, alien, [22.0, 22.0], "green")
p = draw_pixels(p, alien, [-22.0, 0.0], "blue")
p = draw_pixels(p, alien, [0.0, 0.0], "blue")
p = draw_pixels(p, alien, [22.0, 0.0], "blue")
p = draw_pixels(p, alien, [-22.0, -22.0], "red")
p = draw_pixels(p, alien, [0.0, -22.0], "red")
p = draw_pixels(p, alien, [22.0, -22.0], "red")

text = logo.text_3d("ALIEN MONSTERS", depth=10.0)
text.points *= 4.0
text.translate([-20.0, 24.0, 0.0], inplace=True)

p.add_mesh(text, color="yellow")
p.show(cpos="xy")
</code></pre>
<p id="bkmrk--12"><a href="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/image-1682302016371.png"><img src="http://huongdan.fit.vlute.edu.vn/uploads/images/gallery/2023-04/scaled-1680-/image-1682302016371.png" alt=""></a></p>

    </div>        </div>
        <div component="pointer"
     option:pointer:page-id="100"
     id="pointer"
     class="pointer-container">
    <div class="pointer anim " >
        <span class="icon mr-xxs"><svg class="svg-icon" data-icon="link" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M3.9 12c0-1.71 1.39-3.1 3.1-3.1h4V7H7c-2.76 0-5 2.24-5 5s2.24 5 5 5h4v-1.9H7c-1.71 0-3.1-1.39-3.1-3.1zM8 13h8v-2H8v2zm9-6h-4v1.9h4c1.71 0 3.1 1.39 3.1 3.1s-1.39 3.1-3.1 3.1h-4V17h4c2.76 0 5-2.24 5-5s-2.24-5-5-5z"/>
</svg> <svg class="svg-icon" data-icon="include" role="presentation" style="display:none;"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 .5h24v24H0z" fill="none"/>
    <path d="M12 16.5l4-4h-3v-9h-2v9H8l4 4zm9-13h-6v1.99h6v14.03H3V5.49h6V3.5H3c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h18c1.1 0 2-.9 2-2v-14c0-1.1-.9-2-2-2z"/>
</svg></span>
        <div class="input-group inline block">
            <input readonly="readonly" type="text" id="pointer-url" placeholder="url">
            <button class="button outline icon" data-clipboard-target="#pointer-url" type="button" title="Copy Link"><svg class="svg-icon" data-icon="copy" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm3 4H8c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h11c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm0 16H8V7h11v14z"/>
</svg></button>
        </div>
            </div>
</div>    </main>

    <div id="sibling-navigation" class="grid half collapse-xs items-center mb-m px-m no-row-gap fade-in-when-active print-hidden">
    <div>
                    <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/chapter/chapter-2-pyvista" data-shortcut="previous" class="outline-hover no-link-style block rounded">
                <div class="px-m pt-xs text-muted">Previous</div>
                <div class="inline-block">
                    <div class="icon-list-item no-hover">
                        <span class="text-chapter "><svg class="svg-icon" data-icon="chapter" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M4 6H2v14c0 1.1.9 2 2 2h14v-2H4V6zm16-4H8c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-1 9H9V9h10v2zm-4 4H9v-2h6v2zm4-8H9V5h10v2z"/>
</svg></span>
                        <span>Chapter 2: PyVista</span>
                    </div>
                </div>
            </a>
            </div>
    <div>
                    <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/02-mesh-creation-platonic-solids-va-polydata" data-shortcut="next" class="outline-hover no-link-style block rounded text-xs-right">
                <div class="px-m pt-xs text-muted text-xs-right">Next</div>
                <div class="inline block">
                    <div class="icon-list-item no-hover">
                        <span class="text-page "><svg class="svg-icon" data-icon="page" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/>
</svg></span>
                        <span>02. Mesh Creation - Platonic Solids và PolyData</span>
                    </div>
                </div>
            </a>
            </div>
</div>
                </div>
        </div>

        <div class="tri-layout-right print-hidden">
            <aside class="tri-layout-right-contents">
                    <!-- <div id="page-details" class="entity-details mb-xl">
        <h5>Details</h5>
        <div class="blended-links">
            <div class="entity-meta">
    
            <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/01-create-mesh-geometric-objects/revisions" class="entity-meta-item">
            <svg class="svg-icon" data-icon="history" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M13 3c-4.97 0-9 4.03-9 9H1l3.89 3.89.07.14L9 12H6c0-3.87 3.13-7 7-7s7 3.13 7 7-3.13 7-7 7c-1.93 0-3.68-.79-4.94-2.06l-1.42 1.42C8.27 19.99 10.51 21 13 21c4.97 0 9-4.03 9-9s-4.03-9-9-9zm-1 5v5l4.28 2.54.72-1.21-3.5-2.08V8H12z"/>
</svg>Revision #7
        </a>
    
    
            <div class="entity-meta-item">
            <svg class="svg-icon" data-icon="star" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg>            <div>
                Created <span title="Sun, Apr 23, 2023 5:55 AM">2 months ago</span> by <a href='http://huongdan.fit.vlute.edu.vn/user/hoangquyen'>HoangQuyen</a>
            </div>
        </div>
    
            <div class="entity-meta-item">
            <svg class="svg-icon" data-icon="edit" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg>            <div>
                Updated <span title="Mon, Apr 24, 2023 7:56 AM">2 months ago</span> by <a href='http://huongdan.fit.vlute.edu.vn/user/hoangquyen'>HoangQuyen</a>
            </div>
        </div>
    
    </div>
                            <div class="active-restriction">
                                            <div class="entity-meta-item">
                            <svg class="svg-icon" data-icon="lock" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <defs>
        <path d="M0 0h24v24H0V0z" id="a"/>
    </defs>
    <clipPath id="b">
        <use overflow="visible" xlink:href="#a"/>
    </clipPath>
    <path clip-path="url(#b)" d="M12 17c1.1 0 2-.9 2-2s-.9-2-2-2-2 .9-2 2 .9 2 2 2zm6-9h-1V6c0-2.76-2.24-5-5-5S7 3.24 7 6v2H6c-1.1 0-2 .9-2 2v10c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V10c0-1.1-.9-2-2-2zM8.9 6c0-1.71 1.39-3.1 3.1-3.1s3.1 1.39 3.1 3.1v2H8.9V6zM18 20H6V10h12v10z"/>
</svg>                            <div>Book Permissions Active</div>
                        </div>
                                    </div>
            
            
            
                    </div>
    </div> -->

    <div class="actions mb-xl">
        <h5>Actions</h5>

        <div class="icon-list text-link">

            
                                                <a href="http://huongdan.fit.vlute.edu.vn/books/th1345-mo-hinh-hoa-hinh-hoc-3d/page/01-create-mesh-geometric-objects/revisions" data-shortcut="revisions" class="icon-list-item">
                <span><svg class="svg-icon" data-icon="history" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M0 0h24v24H0z" fill="none"/>
    <path d="M13 3c-4.97 0-9 4.03-9 9H1l3.89 3.89.07.14L9 12H6c0-3.87 3.13-7 7-7s7 3.13 7 7-3.13 7-7 7c-1.93 0-3.68-.79-4.94-2.06l-1.42 1.42C8.27 19.99 10.51 21 13 21c4.97 0 9-4.03 9-9s-4.03-9-9-9zm-1 5v5l4.28 2.54.72-1.21-3.5-2.08V8H12z"/>
</svg></span>
                <span>Revisions</span>
            </a>
                        
            <hr class="primary-background"/>

                                </div>

    </div>
            </aside>
        </div>
    </div>

    </div>

    
    <div component="back-to-top" class="back-to-top print-hidden">
        <div class="inner">
            <svg class="svg-icon" data-icon="chevron-up" role="presentation"  viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M7.41 15.41L12 10.83l4.59 4.58L18 14l-6-6-6 6z"/>
    <path d="M0 0h24v24H0z" fill="none"/>
</svg> <span>Back to top</span>
        </div>
    </div>

        <script src="http://huongdan.fit.vlute.edu.vn/dist/app.js?version=v23.01.1" nonce="lBkCpI7kVa2AOtkMAxsWkAP6"></script>
    
    </body>
</html>
