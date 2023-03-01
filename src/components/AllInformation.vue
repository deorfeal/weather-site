<template>
    <div class="all-information">
        <div class="all-information__top all-information-top">
            <h1 class="all-information-top__title">
                WHEATHER DR
            </h1>
            <div class="all-information-top__settings all-information-top-settings">
                <button ref="buttonC" @click="toCelsiuses"
                    class="all-information-top-settings__c all-information-top-settings--active">
                    °C
                </button>
                <button ref="buttonF" @click="toFahrenheits" class="all-information-top-settings__f">
                    °F
                </button>
                <button @click="this.$emit('doDarkMode')" class="all-information-top-settings__mode">
                    <svg class="all-information-top-settings__mode-moon" width="24px" height="24px" viewBox="0 0 24 24"
                        fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M2.03009 12.42C2.39009 17.57 6.76009 21.76 11.9901 21.99C15.6801 22.15 18.9801 20.43 20.9601 17.72C21.7801 16.61 21.3401 15.87 19.9701 16.12C19.3001 16.24 18.6101 16.29 17.8901 16.26C13.0001 16.06 9.00009 11.97 8.98009 7.13996C8.97009 5.83996 9.24009 4.60996 9.73009 3.48996C10.2701 2.24996 9.62009 1.65996 8.37009 2.18996C4.41009 3.85996 1.70009 7.84996 2.03009 12.42Z"
                            stroke="#292D32" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                    <svg class="all-information-top-settings__mode-sun" width="24px" height="24px" viewBox="0 0 24 24"
                        fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M6.0523 4.60639L5.66212 4.21461C5.27194 3.82283 4.64166 3.83288 4.26148 4.21461L4.25148 4.22466C3.8613 4.61644 3.8613 5.24931 4.25148 5.63105L4.64166 6.02283C5.03183 6.41461 5.65211 6.41461 6.04229 6.02283L6.0523 6.01278C6.44247 5.63105 6.44247 4.98813 6.0523 4.60639ZM3.01091 10.9954H1.99045C1.4402 10.9954 1 11.4374 1 11.99V12C1 12.5525 1.4402 12.9945 1.99045 12.9945H3.00091C3.56116 13.0046 4.00136 12.5626 4.00136 12.01V12C4.00136 11.4374 3.56116 10.9954 3.01091 10.9954ZM12.015 1H12.005C11.4447 1 11.0045 1.44201 11.0045 1.99452V2.9589C11.0045 3.51142 11.4447 3.95342 11.995 3.95342H12.005C12.5653 3.96347 13.0055 3.52146 13.0055 2.96895V1.99452C13.0055 1.44201 12.5653 1 12.015 1ZM19.7585 4.22466C19.3683 3.83288 18.7381 3.83288 18.3479 4.21461L17.9577 4.60639C17.5675 4.99817 17.5675 5.63105 17.9577 6.01278L17.9677 6.02283C18.3579 6.41461 18.9882 6.41461 19.3684 6.02283L19.7585 5.63105C20.1487 5.23927 20.1487 4.61644 19.7585 4.22466ZM17.9477 19.3936L18.3379 19.7854C18.7281 20.1772 19.3583 20.1772 19.7485 19.7854C20.1387 19.3936 20.1387 18.7607 19.7485 18.3689L19.3583 17.9772C18.9682 17.5854 18.3379 17.5954 17.9577 17.9772C17.5575 18.379 17.5575 19.0018 17.9477 19.3936ZM20.0086 11.99V12C20.0086 12.5525 20.4488 12.9945 20.9991 12.9945H22.0096C22.5598 12.9945 23 12.5525 23 12V11.99C23 11.4374 22.5598 10.9954 22.0096 10.9954H20.9991C20.4488 10.9954 20.0086 11.4374 20.0086 11.99ZM12.005 5.9726C8.6935 5.9726 6.00227 8.67489 6.00227 12C6.00227 15.3251 8.6935 18.0274 12.005 18.0274C15.3165 18.0274 18.0077 15.3251 18.0077 12C18.0077 8.67489 15.3165 5.9726 12.005 5.9726ZM11.995 23H12.005C12.5553 23 12.9955 22.558 12.9955 22.0055V21.0411C12.9955 20.4886 12.5553 20.0466 12.005 20.0466H11.995C11.4447 20.0466 11.0045 20.4886 11.0045 21.0411V22.0055C11.0045 22.558 11.4447 23 11.995 23ZM4.25148 19.7753C4.64166 20.1671 5.27194 20.1671 5.66212 19.7753L6.0523 19.3836C6.44247 18.9918 6.43247 18.3589 6.0523 17.9772L6.04229 17.9671C5.65211 17.5753 5.02183 17.5753 4.63165 17.9671L4.24147 18.3589C3.8613 18.7607 3.8613 19.3836 4.25148 19.7753Z"
                            fill="white" />
                    </svg>
                </button>
                <!-- <button class="all-information-top-settings__btn">
                    <svg width="25px" height="25px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M12 15C13.6569 15 15 13.6569 15 12C15 10.3431 13.6569 9 12 9C10.3431 9 9 10.3431 9 12C9 13.6569 10.3431 15 12 15Z"
                            stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                        <path
                            d="M18.7273 14.7273C18.6063 15.0015 18.5702 15.3056 18.6236 15.6005C18.6771 15.8954 18.8177 16.1676 19.0273 16.3818L19.0818 16.4364C19.2509 16.6052 19.385 16.8057 19.4765 17.0265C19.568 17.2472 19.6151 17.4838 19.6151 17.7227C19.6151 17.9617 19.568 18.1983 19.4765 18.419C19.385 18.6397 19.2509 18.8402 19.0818 19.0091C18.913 19.1781 18.7124 19.3122 18.4917 19.4037C18.271 19.4952 18.0344 19.5423 17.7955 19.5423C17.5565 19.5423 17.3199 19.4952 17.0992 19.4037C16.8785 19.3122 16.678 19.1781 16.5091 19.0091L16.4545 18.9545C16.2403 18.745 15.9682 18.6044 15.6733 18.5509C15.3784 18.4974 15.0742 18.5335 14.8 18.6545C14.5311 18.7698 14.3018 18.9611 14.1403 19.205C13.9788 19.4489 13.8921 19.7347 13.8909 20.0273V20.1818C13.8909 20.664 13.6994 21.1265 13.3584 21.4675C13.0174 21.8084 12.5549 22 12.0727 22C11.5905 22 11.1281 21.8084 10.7871 21.4675C10.4461 21.1265 10.2545 20.664 10.2545 20.1818V20.1C10.2475 19.7991 10.1501 19.5073 9.97501 19.2625C9.79991 19.0176 9.55521 18.8312 9.27273 18.7273C8.99853 18.6063 8.69437 18.5702 8.39947 18.6236C8.10456 18.6771 7.83244 18.8177 7.61818 19.0273L7.56364 19.0818C7.39478 19.2509 7.19425 19.385 6.97353 19.4765C6.7528 19.568 6.51621 19.6151 6.27727 19.6151C6.03834 19.6151 5.80174 19.568 5.58102 19.4765C5.36029 19.385 5.15977 19.2509 4.99091 19.0818C4.82186 18.913 4.68775 18.7124 4.59626 18.4917C4.50476 18.271 4.45766 18.0344 4.45766 17.7955C4.45766 17.5565 4.50476 17.3199 4.59626 17.0992C4.68775 16.8785 4.82186 16.678 4.99091 16.5091L5.04545 16.4545C5.25503 16.2403 5.39562 15.9682 5.4491 15.6733C5.50257 15.3784 5.46647 15.0742 5.34545 14.8C5.23022 14.5311 5.03887 14.3018 4.79497 14.1403C4.55107 13.9788 4.26526 13.8921 3.97273 13.8909H3.81818C3.33597 13.8909 2.87351 13.6994 2.53253 13.3584C2.19156 13.0174 2 12.5549 2 12.0727C2 11.5905 2.19156 11.1281 2.53253 10.7871C2.87351 10.4461 3.33597 10.2545 3.81818 10.2545H3.9C4.2009 10.2475 4.49273 10.1501 4.73754 9.97501C4.98236 9.79991 5.16883 9.55521 5.27273 9.27273C5.39374 8.99853 5.42984 8.69437 5.37637 8.39947C5.3229 8.10456 5.18231 7.83244 4.97273 7.61818L4.91818 7.56364C4.74913 7.39478 4.61503 7.19425 4.52353 6.97353C4.43203 6.7528 4.38493 6.51621 4.38493 6.27727C4.38493 6.03834 4.43203 5.80174 4.52353 5.58102C4.61503 5.36029 4.74913 5.15977 4.91818 4.99091C5.08704 4.82186 5.28757 4.68775 5.50829 4.59626C5.72901 4.50476 5.96561 4.45766 6.20455 4.45766C6.44348 4.45766 6.68008 4.50476 6.9008 4.59626C7.12152 4.68775 7.32205 4.82186 7.49091 4.99091L7.54545 5.04545C7.75971 5.25503 8.03183 5.39562 8.32674 5.4491C8.62164 5.50257 8.9258 5.46647 9.2 5.34545H9.27273C9.54161 5.23022 9.77093 5.03887 9.93245 4.79497C10.094 4.55107 10.1807 4.26526 10.1818 3.97273V3.81818C10.1818 3.33597 10.3734 2.87351 10.7144 2.53253C11.0553 2.19156 11.5178 2 12 2C12.4822 2 12.9447 2.19156 13.2856 2.53253C13.6266 2.87351 13.8182 3.33597 13.8182 3.81818V3.9C13.8193 4.19253 13.906 4.47834 14.0676 4.72224C14.2291 4.96614 14.4584 5.15749 14.7273 5.27273C15.0015 5.39374 15.3056 5.42984 15.6005 5.37637C15.8954 5.3229 16.1676 5.18231 16.3818 4.97273L16.4364 4.91818C16.6052 4.74913 16.8057 4.61503 17.0265 4.52353C17.2472 4.43203 17.4838 4.38493 17.7227 4.38493C17.9617 4.38493 18.1983 4.43203 18.419 4.52353C18.6397 4.61503 18.8402 4.74913 19.0091 4.91818C19.1781 5.08704 19.3122 5.28757 19.4037 5.50829C19.4952 5.72901 19.5423 5.96561 19.5423 6.20455C19.5423 6.44348 19.4952 6.68008 19.4037 6.9008C19.3122 7.12152 19.1781 7.32205 19.0091 7.49091L18.9545 7.54545C18.745 7.75971 18.6044 8.03183 18.5509 8.32674C18.4974 8.62164 18.5335 8.9258 18.6545 9.2V9.27273C18.7698 9.54161 18.9611 9.77093 19.205 9.93245C19.4489 10.094 19.7347 10.1807 20.0273 10.1818H20.1818C20.664 10.1818 21.1265 10.3734 21.4675 10.7144C21.8084 11.0553 22 11.5178 22 12C22 12.4822 21.8084 12.9447 21.4675 13.2856C21.1265 13.6266 20.664 13.8182 20.1818 13.8182H20.1C19.8075 13.8193 19.5217 13.906 19.2778 14.0676C19.0339 14.2291 18.8425 14.4584 18.7273 14.7273Z"
                            stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                </button> -->
            </div>
        </div>
        <div class="all-information__items all-information-items">
            <swiper class="all-information-items__swiper" :slides-per-view="this.slidesPerView"
                :space-between="this.slidesSpace" @swiper="onSwiper" @slideChange="onSlideChange">
                <swiper-slide v-for="item in weatherDaysInf" :key="item.datetimeEpoch">
                    <InformationItem :daysData="item" />
                </swiper-slide>
            </swiper>
        </div>
        <div class="all-information__today inf-today">
            <h2 class="inf-today__title">
                Today's Highlights
            </h2>
            <div class="inf-today__inner">
                <div class="inf-today__item inf-today-item">
                    <p class="inf-today-item__text">
                        UV Index
                    </p>
                    <svg class="inf-today-item__uv" width="80px" height="80px" viewBox="0 0 22 22"
                        xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:cc="http://creativecommons.org/ns#"
                        xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns="http://www.w3.org/2000/svg"
                        xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd"
                        xmlns:inkscape="http://www.inkscape.org/namespaces/inkscape" id="svg4355" version="1.1"
                        inkscape:version="1.0.1 (3bc2e813f5, 2020-09-07)" sodipodi:docname="dark_zoom-fit-curve.svg">

                        <sodipodi:namedview id="base" pagecolor="#ffffff" bordercolor="#666666" borderopacity="1.0"
                            inkscape:pageopacity="0.0" inkscape:pageshadow="2" inkscape:zoom="23.05398"
                            inkscape:cx="12.391156" inkscape:cy="7.156479" inkscape:document-units="px"
                            inkscape:current-layer="layer1" showgrid="true" width="0px" height="0px" fit-margin-top="0"
                            fit-margin-left="0" fit-margin-right="0" fit-margin-bottom="0" inkscape:window-width="2560"
                            inkscape:window-height="1376" inkscape:window-x="0" inkscape:window-y="0"
                            inkscape:window-maximized="1" inkscape:showpageshadow="false" inkscape:document-rotation="0">

                            <inkscape:grid type="xygrid" id="grid4114" />

                            <sodipodi:guide position="2.0000011,19.999996" orientation="18,0" id="guide4120"
                                inkscape:locked="false" />

                            <sodipodi:guide position="2.0000011,1.9999962" orientation="0,18" id="guide4122"
                                inkscape:locked="false" />

                            <sodipodi:guide position="20.000001,1.9999962" orientation="-18,0" id="guide4124"
                                inkscape:locked="false" />

                            <sodipodi:guide position="20.000001,19.999996" orientation="0,-18" id="guide4126"
                                inkscape:locked="false" />

                            <sodipodi:guide position="3.0000011,18.999996" orientation="16,0" id="guide4128"
                                inkscape:locked="false" />

                            <sodipodi:guide position="3.0000011,2.9999962" orientation="0,16" id="guide4130"
                                inkscape:locked="false" />

                            <sodipodi:guide position="19.000001,2.9999962" orientation="-16,0" id="guide4132"
                                inkscape:locked="false" />

                            <sodipodi:guide position="19.000001,18.999996" orientation="0,-16" id="guide4134"
                                inkscape:locked="false" />

                        </sodipodi:namedview>

                        <metadata id="metadata4360">

                            <rdf:RDF>

                                <cc:Work>

                                    <dc:format>image/svg+xml</dc:format>

                                    <dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage" />

                                    <dc:title />

                                    <dc:date>2016</dc:date>

                                    <dc:creator>

                                        <cc:Agent>

                                            <dc:title>Timothée Giet</dc:title>

                                        </cc:Agent>

                                    </dc:creator>

                                    <cc:license rdf:resource="http://creativecommons.org/licenses/by-sa/4.0/" />

                                </cc:Work>

                                <cc:License rdf:about="http://creativecommons.org/licenses/by-sa/4.0/">

                                    <cc:permits rdf:resource="http://creativecommons.org/ns#Reproduction" />

                                    <cc:permits rdf:resource="http://creativecommons.org/ns#Distribution" />

                                    <cc:requires rdf:resource="http://creativecommons.org/ns#Notice" />

                                    <cc:requires rdf:resource="http://creativecommons.org/ns#Attribution" />

                                    <cc:permits rdf:resource="http://creativecommons.org/ns#DerivativeWorks" />

                                    <cc:requires rdf:resource="http://creativecommons.org/ns#ShareAlike" />

                                </cc:License>

                            </rdf:RDF>

                        </metadata>

                        <g inkscape:label="Capa 1" inkscape:groupmode="layer" id="layer1"
                            transform="translate(-544.571 -742.934)">

                            <path style="opacity:1;fill:#373737;fill-opacity:1;stroke:none"
                                d="M547.571 745.934v4h1v-3h3v-1h-3z" id="path4162" inkscape:connector-curvature="0"
                                sodipodi:nodetypes="ccccccccc" />

                            <path style="opacity:1;fill:#373737;fill-opacity:1;stroke:none"
                                d="M562.571 757.934v3h-3v1h4v-4z" id="rect4134" inkscape:connector-curvature="0"
                                sodipodi:nodetypes="cccccccc" />

                            <path sodipodi:nodetypes="ccccccccc" inkscape:connector-curvature="0" id="path4170"
                                d="M563.571 745.934v4h-1v-3h-3v-1h3z"
                                style="opacity:1;fill:#373737;fill-opacity:1;stroke:none" />

                            <path sodipodi:nodetypes="cccccccc" inkscape:connector-curvature="0" id="path4172"
                                d="M548.571 757.934v3h3v1h-4v-4z"
                                style="opacity:1;fill:#373737;fill-opacity:1;stroke:none" />

                            <path
                                style="fill:none;stroke:#373737;stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1"
                                d="M550.571 758.934c5 0 5-5 5-5s0-5 5-5" id="path1609" sodipodi:nodetypes="ccc" />

                        </g>

                    </svg>
                    <p class="inf-today-item__digit">
                        {{ this.weatherDataInf.uvindex }}
                    </p>
                </div>
                <div class="inf-today__item inf-today-item">
                    <p class="inf-today-item__text">
                        Wind Status
                    </p>
                    <p class="inf-today-item__km">
                        <span>
                            {{ this.weatherDataInf.windspeed }}
                        </span>
                        <span>
                            km/h
                        </span>
                    </p>
                    <svg class="inf-today-item__wind" width="40px" height="40px" viewBox="0 0 24 24" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M2 15H18.5C20.43 15 22 16.57 22 18.5C22 20.43 20.43 22 18.5 22C16.57 22 15 20.43 15 18.5V18"
                            stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round"
                            stroke-linejoin="round" />
                        <path d="M2 12H18.5C20.42 12 22 10.43 22 8.5C22 6.58 20.42 5 18.5 5C16.58 5 15 6.57 15 8.5V9"
                            stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round"
                            stroke-linejoin="round" />
                        <path
                            d="M2 9H9.31C10.8 9 12 7.79 12 6.31C12 4.82 10.79 3.62 9.31 3.62C7.82 3.62 6.62 4.83 6.62 6.31V6.69"
                            stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round"
                            stroke-linejoin="round" />
                    </svg>
                </div>
                <div class="inf-today__item inf-today-item">
                    <p class="inf-today-item__text">
                        Sunrise &#38; Sunset
                    </p>
                    <div class="inf-today-item__column inf-today-item-column">
                        <div class="inf-today-item-column__row inf-today-item-column-row">
                            <svg class="inf-today-item-column-row__svg" width="24" height="24" viewBox="0 0 24 24"
                                fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M6.0523 4.60639L5.66212 4.21461C5.27194 3.82283 4.64166 3.83288 4.26148 4.21461L4.25148 4.22466C3.8613 4.61644 3.8613 5.24931 4.25148 5.63105L4.64166 6.02283C5.03183 6.41461 5.65211 6.41461 6.04229 6.02283L6.0523 6.01278C6.44247 5.63105 6.44247 4.98813 6.0523 4.60639ZM3.01091 10.9954H1.99045C1.4402 10.9954 1 11.4374 1 11.99V12C1 12.5525 1.4402 12.9945 1.99045 12.9945H3.00091C3.56116 13.0046 4.00136 12.5626 4.00136 12.01V12C4.00136 11.4374 3.56116 10.9954 3.01091 10.9954ZM12.015 1H12.005C11.4447 1 11.0045 1.44201 11.0045 1.99452V2.9589C11.0045 3.51142 11.4447 3.95342 11.995 3.95342H12.005C12.5653 3.96347 13.0055 3.52146 13.0055 2.96895V1.99452C13.0055 1.44201 12.5653 1 12.015 1ZM19.7585 4.22466C19.3683 3.83288 18.7381 3.83288 18.3479 4.21461L17.9577 4.60639C17.5675 4.99817 17.5675 5.63105 17.9577 6.01278L17.9677 6.02283C18.3579 6.41461 18.9882 6.41461 19.3684 6.02283L19.7585 5.63105C20.1487 5.23927 20.1487 4.61644 19.7585 4.22466ZM17.9477 19.3936L18.3379 19.7854C18.7281 20.1772 19.3583 20.1772 19.7485 19.7854C20.1387 19.3936 20.1387 18.7607 19.7485 18.3689L19.3583 17.9772C18.9682 17.5854 18.3379 17.5954 17.9577 17.9772C17.5575 18.379 17.5575 19.0018 17.9477 19.3936ZM20.0086 11.99V12C20.0086 12.5525 20.4488 12.9945 20.9991 12.9945H22.0096C22.5598 12.9945 23 12.5525 23 12V11.99C23 11.4374 22.5598 10.9954 22.0096 10.9954H20.9991C20.4488 10.9954 20.0086 11.4374 20.0086 11.99ZM12.005 5.9726C8.6935 5.9726 6.00227 8.67489 6.00227 12C6.00227 15.3251 8.6935 18.0274 12.005 18.0274C15.3165 18.0274 18.0077 15.3251 18.0077 12C18.0077 8.67489 15.3165 5.9726 12.005 5.9726ZM11.995 23H12.005C12.5553 23 12.9955 22.558 12.9955 22.0055V21.0411C12.9955 20.4886 12.5553 20.0466 12.005 20.0466H11.995C11.4447 20.0466 11.0045 20.4886 11.0045 21.0411V22.0055C11.0045 22.558 11.4447 23 11.995 23ZM4.25148 19.7753C4.64166 20.1671 5.27194 20.1671 5.66212 19.7753L6.0523 19.3836C6.44247 18.9918 6.43247 18.3589 6.0523 17.9772L6.04229 17.9671C5.65211 17.5753 5.02183 17.5753 4.63165 17.9671L4.24147 18.3589C3.8613 18.7607 3.8613 19.3836 4.25148 19.7753Z"
                                    fill="white" />
                            </svg>
                            <div class="inf-today-item-column-row__box">
                                <div class="inf-today-item-column-row__box-sunrise">
                                    {{ currentSunrise }}
                                    AM
                                    <!-- <span class="inf-today-item-column-row__box-sunrise-minus">
                                        -1m 32s
                                    </span> -->
                                </div>
                            </div>
                        </div>
                        <div class="inf-today-item-column__row inf-today-item-column-row">
                            <svg class="inf-today-item-column-row__svg" width="20" height="20" viewBox="0 0 24 24"
                                fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M17.7499 4.08998L15.2199 6.02998L16.1299 9.08998L13.4999 7.27998L10.8699 9.08998L11.7799 6.02998L9.24995 4.08998L12.4399 3.99998L13.4999 0.999977L14.5599 3.99998L17.7499 4.08998ZM21.2499 11L19.6099 12.25L20.1999 14.23L18.4999 13.06L16.7999 14.23L17.3899 12.25L15.7499 11L17.8099 10.95L18.4999 8.99998L19.1899 10.95L21.2499 11ZM18.9699 15.95C19.7999 15.87 20.6899 17.05 20.1599 17.8C19.8399 18.25 19.4999 18.67 19.0799 19.07C15.1699 23 8.83995 23 4.93995 19.07C1.02995 15.17 1.02995 8.82998 4.93995 4.92998C5.33995 4.52998 5.75995 4.16998 6.20995 3.84998C6.95995 3.31998 8.13995 4.20998 8.05995 5.03998C7.78995 7.89998 8.74995 10.87 10.9499 13.06C13.1399 15.26 16.0999 16.22 18.9699 15.95Z"
                                    fill="white" />
                            </svg>
                            <div class="inf-today-item-column-row__box">
                                <div class="inf-today-item-column-row__box-sunset">
                                    {{ currentSunset }}
                                    PM
                                    <!-- <span class="inf-today-item-column-row__box-sunrise-plus">
                                        +2m 43s
                                    </span> -->
                                </div>
                            </div>
                        </div>
                    </div>
                    <span></span>
                </div>
                <div class="inf-today__item inf-today-item">
                    <p class="inf-today-item__text">
                        Humidity
                    </p>
                    <p class="inf-today-item__digits">
                        <span>{{ this.weatherDataInf.humidity }}</span>
                        <span>%</span>
                    </p>
                    <!-- <div class="inf-today-item__row">
                        <svg fill="#000000" width="15px" height="15px" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M22.707,6.436A1,1,0,1,1,21.293,7.85a13.141,13.141,0,0,0-18.586,0A1,1,0,0,1,1.293,6.436a15.14,15.14,0,0,1,21.414,0Zm-3.333,3.642a10.427,10.427,0,0,0-14.748,0,1,1,0,0,0,1.415,1.414,8.426,8.426,0,0,1,11.918,0,1,1,0,0,0,1.415-1.414Zm-4.041,5.3a1,1,0,0,0,.708-1.707,5.714,5.714,0,0,0-8.082,0,1,1,0,1,0,1.415,1.414,3.8,3.8,0,0,1,5.252,0A1,1,0,0,0,15.333,15.381ZM13.5,19.5A1.5,1.5,0,1,0,12,21,1.5,1.5,0,0,0,13.5,19.5Z" />
                        </svg>
                        <p class="inf-today-item__row-text">No data</p>
                    </div> -->
                    <span></span>
                </div>
                <div class="inf-today__item inf-today-item">
                    <p class="inf-today-item__text">
                        Visibility
                    </p>
                    <p class="inf-today-item__digits">
                        <span>{{ this.weatherDataInf.visibility }}</span>
                        <span>km</span>
                    </p>
                    <!-- <div class="inf-today-item__row">
                        <svg fill="#000000" width="15px" height="15px" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M22.707,6.436A1,1,0,1,1,21.293,7.85a13.141,13.141,0,0,0-18.586,0A1,1,0,0,1,1.293,6.436a15.14,15.14,0,0,1,21.414,0Zm-3.333,3.642a10.427,10.427,0,0,0-14.748,0,1,1,0,0,0,1.415,1.414,8.426,8.426,0,0,1,11.918,0,1,1,0,0,0,1.415-1.414Zm-4.041,5.3a1,1,0,0,0,.708-1.707,5.714,5.714,0,0,0-8.082,0,1,1,0,1,0,1.415,1.414,3.8,3.8,0,0,1,5.252,0A1,1,0,0,0,15.333,15.381ZM13.5,19.5A1.5,1.5,0,1,0,12,21,1.5,1.5,0,0,0,13.5,19.5Z" />
                        </svg>
                        <p class="inf-today-item__row-text">No data</p>
                    </div> -->
                    <span></span>
                </div>
                <div class="inf-today__item inf-today-item">
                    <p class="inf-today-item__text">
                        Pressure
                    </p>
                    <p class="inf-today-item__digits">
                        <span> {{ this.weatherDataInf.pressure }}</span>
                    </p>
                    <!-- <div class="inf-today-item__row">
                        <svg fill="#000000" width="15px" height="15px" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M22.707,6.436A1,1,0,1,1,21.293,7.85a13.141,13.141,0,0,0-18.586,0A1,1,0,0,1,1.293,6.436a15.14,15.14,0,0,1,21.414,0Zm-3.333,3.642a10.427,10.427,0,0,0-14.748,0,1,1,0,0,0,1.415,1.414,8.426,8.426,0,0,1,11.918,0,1,1,0,0,0,1.415-1.414Zm-4.041,5.3a1,1,0,0,0,.708-1.707,5.714,5.714,0,0,0-8.082,0,1,1,0,1,0,1.415,1.414,3.8,3.8,0,0,1,5.252,0A1,1,0,0,0,15.333,15.381ZM13.5,19.5A1.5,1.5,0,1,0,12,21,1.5,1.5,0,0,0,13.5,19.5Z" />
                        </svg>
                        <p class="inf-today-item__row-text">No data</p>
                    </div> -->
                    <span></span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import InformationItem from './InformationItem.vue'

import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';

export default {
    name: 'AllInformation',
    components: {
        InformationItem,
        Swiper,
        SwiperSlide,
    },
    props: ['weatherDataInf', 'weatherDaysInf', 'weatherRawInf'],
    inject: ['fahrenheits'],
    data() {
        return {
            slidesPerView: 6,
            widthOfWindow: 0,
            slidesSpace: 20,
        }
    },
    computed: {
        currentSunrise() {
            return String(this.weatherDataInf.sunrise).slice(0, 5)
        },
        currentSunset() {
            return String(this.weatherDataInf.sunset).slice(0, 5)
        }
    },
    setup() {
        const onSwiper = (swiper) => {
            // console.log(swiper);
        };
        const onSlideChange = () => {
            // console.log('slide change');
        };
        return {
            onSwiper,
            onSlideChange,
        };
    },
    mounted() {
        this.widthOfWindow = window.innerWidth

        if (this.widthOfWindow == 1550 || this.widthOfWindow < 1550) {
            this.slidesPerView = 6
            if (this.widthOfWindow == 1250 || this.widthOfWindow < 1200) {
                this.slidesPerView = 5
                if (this.widthOfWindow == 1000 || this.widthOfWindow < 1000) {
                    this.slidesPerView = 4
                    if (this.widthOfWindow == 800 || this.widthOfWindow < 800) {
                        this.slidesPerView = 5
                        this.slidesSpace = 10
                        if (this.widthOfWindow == 650 || this.widthOfWindow < 650) {
                            this.slidesPerView = 4
                            if (this.widthOfWindow == 500 || this.widthOfWindow < 500) {
                                this.slidesPerView = 3
                            }
                        }
                    }
                }
            }
        } else {
            this.slidesPerView = 6
        }

        window.addEventListener('resize', (e) => {
            this.widthOfWindow = window.innerWidth
            if (this.widthOfWindow == 1550 || this.widthOfWindow < 1550) {
                this.slidesPerView = 6
                if (this.widthOfWindow == 1250 || this.widthOfWindow < 1200) {
                    this.slidesPerView = 5
                    if (this.widthOfWindow == 1000 || this.widthOfWindow < 1000) {
                        this.slidesPerView = 4
                        if (this.widthOfWindow == 800 || this.widthOfWindow < 800) {
                            this.slidesPerView = 5
                            this.slidesSpace = 10
                            if (this.widthOfWindow == 650 || this.widthOfWindow < 650) {
                                this.slidesPerView = 4
                                if (this.widthOfWindow == 500 || this.widthOfWindow < 500) {
                                    this.slidesPerView = 3
                                }
                            }
                        }
                    }
                }
            } else {
                this.slidesPerView = 6
            }
        })
    },
    methods: {
        toCelsiuses(elem) {
            this.$emit('getСelsiuses')
        },
        toFahrenheits(elem) {
            this.$emit('getFahrenheits')
        }
    },
    watch: {
        fahrenheits: {
            handler() {
                if (this.fahrenheits.value == true) {
                    this.$refs.buttonC.classList.remove('all-information-top-settings--active')
                    this.$refs.buttonF.classList.add('all-information-top-settings--active')
                } else {
                    this.$refs.buttonC.classList.add('all-information-top-settings--active')
                    this.$refs.buttonF.classList.remove('all-information-top-settings--active')
                }
            },
            deep: true
        },
    }
}
</script>

<style lang="scss">
@import '../assets/scss/vars';

.all-information {
    padding: 0px 40px 0 40px;
    overflow: hidden;
    @include adaptiv-value("width", 1120, 320, 1);
}

.all-information-top {
    border: 1px solid #f1f1f1;
    @include adaptiv-value("margin-bottom", 65, 16, 1);
    padding-left: 20px;
    padding-right: 20px;
    background: #fff;
    border-radius: 0 0 20px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    @include adaptiv-value("gap", 40, 20, 1);
    @include adaptiv-value("padding-top", 20, 25, 1);
    @include adaptiv-value("padding-bottom", 20, 10, 1);

    &__title {
        font-weight: 700;
        @include adaptiv-value("font-size", 25, 17, 1);
        @include adaptiv-value("line-height", 30, 21, 1);
    }
}

.all-information-top-settings {
    display: flex;
    align-items: center;
    @include adaptiv-value("gap", 20, 6, 1);
    line-height: 16px;

    &__c {
        &:hover {
            transform: scale(0.95)
        }
        background: #fff;
        border-radius: 45%;
        box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.1);
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 16, 14, 1);
        @include adaptiv-value("padding-top", 6, 4, 1);
        @include adaptiv-value("padding-bottom", 6, 4, 1);
        @include adaptiv-value("padding-left", 10, 8, 1);
        @include adaptiv-value("padding-right", 10, 8, 1);
    }

    &__f {
        transition: transform 0.3s;
        &:hover {
            transform: scale(0.95)
        }
        box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.1);
        background: #fff;
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 16, 14, 1);
        @include adaptiv-value("padding-top", 6, 4, 1);
        @include adaptiv-value("padding-bottom", 6, 4, 1);
        @include adaptiv-value("padding-left", 10, 8, 1);
        @include adaptiv-value("padding-right", 10, 8, 1);
        border-radius: 45%;
    }

    &__mode {

        svg {
            transition: transform 0.3s;
        }

        &:hover {
            svg {
                transform: scale(0.95)
            }
        }
    }

    &__mode-moon {
        display: block;
        @include adaptiv-value("width", 24, 22, 1);
        @include adaptiv-value("height", 24, 22, 1);

        path {
            fill: transparent;
            transition: fill 0.3s;
        }
    }

    &__mode-sun {
        display: none;
        @include adaptiv-value("width", 24, 22, 1);
        @include adaptiv-value("height", 24, 22, 1);
    }


    &__btn {
        @include adaptiv-value("width", 24, 22, 1);
        @include adaptiv-value("height", 24, 22, 1);
        display: flex;
        justify-content: center;
        align-items: center;

        svg {
            @include adaptiv-value("width", 24, 22, 1);
            @include adaptiv-value("height", 24, 22, 1);
            transition: transform 0.3s;
        }

        &:hover {
            svg {
                transform: scale(0.95)
            }
        }
    }
}

.all-information-top-settings--active {
    background: #000;
    color: #fff;
}

.all-information-items {
    display: flex;
    gap: 25px;
    align-items: center;
    @include adaptiv-value("margin-bottom", 30, 10, 1);
    justify-content: center;
    width: 100%;

    &__swiper {
        padding: 50px 30px;
        padding-top: unset;
        padding-bottom: 20px;
        margin-left: 20px;
        margin-right: 20px;
        max-width: 100%;
    }
}

.inf-today {
    &__title {
        @include adaptiv-value("margin-bottom", 15, 10, 1);
        font-weight: 600;
        @include adaptiv-value("font-size", 16, 14, 1);
        @include adaptiv-value("line-height", 18, 16, 1);
    }

    &__inner {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        padding-bottom: 40px;
        @include adaptiv-value("gap", 25, 15, 1);
    }

}

.inf-today-item {
    border: 1px solid #f1f1f1;
    background: #fff;
    padding: 15px;
    border-radius: 10px;
    @include adaptiv-value("min-height", 210, 150, 1);
    box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    transition: transform 0.3s;
    cursor: pointer;
    transition: background 0.3s, border 0.3s, transform 0.3s;
    @include adaptiv-value("padding-bottom", 30, 20, 1);

    &:hover {
        transform: translateY(5%);
    }

    &__uv {
        @include adaptiv-value("width", 80, 60, 1);
        @include adaptiv-value("height", 80, 60, 1);
        filter: none;

        g {
            path {
                fill: #000 !important;
            }

            path:nth-last-child(1) {
                fill: none !important;
                stroke: #000 !important;
            }
        }
    }

    &__wind {
        @include adaptiv-value("width", 40, 25, 1);
        @include adaptiv-value("height", 40, 25, 1);

        path {
            stroke: #000,
        }
    }

    &:hover {
        transform: translateY(2.5%);
    }

    &__text {
        @include adaptiv-value("margin-bottom", 15, 10, 1);
        color: rgb(165, 165, 165);
        align-self: flex-start;

        @include adaptiv-value("font-size", 15, 12, 1);
        @include adaptiv-value("line-height", 18, 14, 1);
    }

    &__img {
        width: 80px;
        height: 80px;
        display: block;
        margin-left: auto;
        margin-right: auto;
        margin-bottom: 15px;
    }

    &__digit {
        margin-left: auto;
        margin-right: auto;
        display: block;
        text-align: center;
        font-weight: 500;

        @include adaptiv-value("font-size", 18, 14, 1);
        @include adaptiv-value("line-height", 20, 16, 1);

    }

    &__km {
        font-weight: 300;
        @include adaptiv-value("font-size", 50, 30, 1);
        @include adaptiv-value("line-height", 60, 30, 1);

        span {}

        span:nth-child(2) {
            @include adaptiv-value("font-size", 16, 12, 1);
            @include adaptiv-value("line-height", 18, 16, 1);
            font-weight: 500;
        }
    }

    &__digits {
        align-self: flex-start;
        font-weight: 300;
        margin-left: auto;
        margin-right: auto;

        @include adaptiv-value("font-size", 50, 30, 1);
        @include adaptiv-value("line-height", 60, 30, 1);

        span {}

        span:nth-child(2) {
            @include adaptiv-value("font-size", 16, 14, 1);
            @include adaptiv-value("line-height", 18, 16, 1);
            font-weight: 500;
            vertical-align: text-top;
        }
    }

    &__row {
        display: flex;
        gap: 10px;
        align-self: flex-start;
    }

    &__row-text {}
}

.inf-today-item-column {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.inf-today-item-column-row {
    display: flex;
    align-items: center;
    @include adaptiv-value("gap", 15, 7, 1);

    &__box {
        display: flex;
        align-items: center;
        gap: 5px;
    }

    &__svg {
        filter: invert(1);
        @include adaptiv-value("width", 25, 18, 1);
        @include adaptiv-value("height", 25, 18, 1);
    }

    &__box-sunrise {
        display: flex;
        flex-direction: column;
        gap: 2px;
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 16, 14, 1);
    }

    &__box-sunrise-minus {
        color: rgb(165, 165, 165);
        @include adaptiv-value("font-size", 11, 9, 1);
        @include adaptiv-value("line-height", 14, 12, 1);
    }

    &__box-sunrise-plus {
        color: rgb(165, 165, 165);
        @include adaptiv-value("font-size", 11, 9, 1);
        @include adaptiv-value("line-height", 14, 12, 1);
    }

    &__box-sunset {
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 16, 14, 1);
        display: flex;
        flex-direction: column;
        gap: 2px;
    }
}

@media (max-width: 1550px) {
    .all-information-items__swiper {
        margin-left: unset;
        margin-right: unset;
        padding-left: unset;
        padding-right: unset;
    }
}

@media (max-width: 1050px) {
    .inf-today__inner {
        grid-template-columns: 1fr 1fr;
    }
}

@media (max-width: 900px) {
    .all-information {
        padding: 0px 20px 0 20px;
    }
}

@media (max-width: 800px) {
    .all-information {
        @include adaptiv-value("width", 1550, 320, 1);
    }

    .all-information-top {
        background: unset !important;
        transition: unset !important;
        border: unset !important;
    }

    .info-panel-view-row {
        display: flex;
        justify-content: space-between;
    }

    .all-information-top {
        padding-left: unset;
        padding-right: unset;
    }
}

@media (max-width: 550px) {
    .inf-today__inner {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 450px) {
    .all-information-top {
        align-items: flex-start;
        gap: 10px;
    }
}
</style>>
