```css [booking_layout.scss]
/* ----------------------------------------------------------------------------

* Easy!Appointments - Online Appointment Scheduler

*

* @package EasyAppointments

* @author A.Tselegidis <alextselegidis@gmail.com>

* @copyright Copyright (c) Alex Tselegidis

* @license https://opensource.org/licenses/GPL-3.0 - GPLv3

* @link https://easyappointments.org

* @since v1.5.0

* ---------------------------------------------------------------------------- */

  

root {

display: block;

}

  

html,

body {

height: 100%;

}

  

#main {

min-height: 100%;

}

  

/* BOOK APPOINTMENT WIZARD

------------------------------------------------------------------------------ */

  

#book-appointment-wizard {

min-height: 480px;

padding: 0;

margin: auto;

}

  

#book-appointment-wizard #header {

overflow: auto;

height: auto;

padding: 20px 15px;

}

  

#book-appointment-wizard #company-name {

float: none;

display: block;

text-align: center;

font-size: 24px;

font-weight: lighter;

color: #fff;

margin: 20px 0;

  

#company-logo {

display: block;

margin: 14px auto;

max-height: 56px;

}

  

.display-booking-selection {

color: #225d4d;

border-right-color: #225d4d !important;

font-size: 60%;

font-weight: normal;

}

}

  

#book-appointment-wizard #steps {

float: none;

display: block;

overflow: auto;

margin: 15px auto;

width: 190px;

}

  

#book-appointment-wizard #book-appointment-form #book-appointment-submit {

width: 100%;

margin-right: 0;

}

  

#book-appointment-wizard #form-message {

text-align: center;

margin-bottom: 30px;

}

  

#book-appointment-wizard .wizard-frame {

height: auto;

padding: 15px;

}

  

#book-appointment-wizard .wizard-frame .frame-container {

height: auto;

min-height: 500px;

padding: 15px 0;

}

  

#book-appointment-wizard .frame-container .frame-title {

font-weight: lighter;

text-align: center;

margin-bottom: 30px;

color: #666;

}

  

#book-appointment-wizard .frame-container .frame-content {

float: none;

}

  

#book-appointment-wizard .wizard-frame .command-buttons {

float: none;

margin: 15px auto;

text-align: center;

}

  

#book-appointment-wizard .wizard-frame .command-buttons .btn {

min-width: 120px;

margin-right: 10px;

}

  

#book-appointment-wizard .wizard-frame .command-buttons .btn:last-child {

margin-right: 0;

}

  

#book-appointment-wizard .wizard-frame .flatpickr-calendar {

margin: 25px auto;

}

  

#book-appointment-wizard .wizard-frame #select-time {

max-width: 288px;

margin: auto;

padding: 15px 0;

}

  

#book-appointment-wizard .book-step {

display: flex;

height: 32px;

width: 32px;

margin-right: 12px;

margin-top: 6px;

border-radius: 0.25rem;

transition: all 0.3s linear;

}

  

#book-appointment-wizard .book-step:last-child {

margin-right: 0;

}

  

#book-appointment-wizard .book-step strong {

font-size: 12px;

display: block;

text-align: center;

color: #0bb98d;

transition: all 0.3s linear;

cursor: default;

}

  

#book-appointment-wizard .active-step {

display: inline-block;

height: 45px;

width: 45px;

background: #65CCE7;

padding: 7px;

margin-right: 13px;

margin-top: 0;

}

  

#book-appointment-wizard .active-step strong {

color: #429a82;

font-size: 21px;

}

  

#book-appointment-wizard #frame-footer {

padding: 15px;

text-align: center;

border-top: 1px solid #ebeef1;

}

  

#book-appointment-wizard #available-hours {

overflow: auto;

margin: 15px 0;

padding-right: 10px;

width: auto;

max-height: 250px;

}

  

#book-appointment-wizard #available-hours div {

margin-right: 30px;

}

  

#book-appointment-wizard #available-hours .available-hour {

margin-bottom: 10px;

}

  

#book-appointment-wizard #available-hours .selected-hour {

background-color: #439a82;

border-color: #439a82;

color: white;

}

  

#book-appointment-wizard .span3 {

min-width: 270px; /* This is especially needed for ie8 */

}

  

#book-appointment-wizard #select-timezone {

margin-bottom: 15px;

}

  

#book-appointment-wizard #appointment-details p,

#book-appointment-wizard #customer-details p {

font-size: 16px;

line-height: 28px;

}

  

#book-appointment-wizard #wizard-frame-1 label {

font-size: 19px;

margin-bottom: 12px;

}

  

#book-appointment-wizard #wizard-frame-1 select {

margin-bottom: 25px;

}

  

#book-appointment-wizard .captcha-title {

float: left;

margin: 7px 0 10px 0;

}

  

#book-appointment-wizard .captcha-title .fa-sync-alt {

cursor: pointer;

transition: all 0.3s linear;

}

  

#book-appointment-wizard .captcha-title .fa-sync-alt:hover {

color: #1a865f;

}

  

#book-appointment-wizard .captcha-image {

float: left;

margin-bottom: 20px;

border-radius: 3px;

}

  

#book-appointment-wizard .captcha-text {

width: 100%;

margin-bottom: 20px;

}

  

#book-appointment-wizard #service-description {

overflow-y: auto;

clear: both;

max-height: 153px;

box-shadow: none;

}

  

#book-appointment-wizard #select-language,

#book-appointment-wizard .backend-link {

display: block;

min-width: 120px;

margin: 15px auto;

padding: 5px;

}

  

.popover .popover-title {

text-align: center;

}

  

.popover .popover-content #language-list .language {

margin: 15px 0;

}

  

#book-appointment-wizard #wizard-frame-4 .frame-container .frame-content {

max-width: 630px;

}

  

@media (min-width: 768px) {

.wrapper {

min-height: 100vh;

}

  

#book-appointment-wizard {

border-radius: 0.25rem;

overflow: hidden;

}

  

#book-appointment-wizard #company-name {

text-align: left;

display: inline-block;

float: left;

margin: 0 auto;

min-width: 400px;

line-height: 1.4;

  

#company-logo {

display: inline-block;

float: left;

margin-right: 14px;

margin-top: 0;

margin-bottom: 0;

}

}

  

#book-appointment-wizard #steps {

display: inline-block;

position: absolute;

left: 50%;

transform: translateX(-50%);

margin: 5px auto;

}

  

#book-appointment-wizard .wizard-frame {

padding: 10px 20px;

}

  

#book-appointment-wizard .wizard-frame .command-buttons {

display: flex;

justify-content: space-between;

}

  

#book-appointment-wizard .captcha-title {

margin-right: 20px;

margin-top: 7px;

}

  

#book-appointment-wizard .captcha-image {

float: right;

}

  

#book-appointment-wizard #select-language {

width: 100px;

padding: 5px;

margin: 5px auto;

}

  

#book-appointment-wizard #frame-footer small {

display: flex;

}

  

#book-appointment-wizard .footer-powered-by,

#book-appointment-wizard .footer-options {

width: 50%;

}

  

#book-appointment-wizard .footer-powered-by {

text-align: left;

padding: 5px 5px 5px 0;

}

  

#book-appointment-wizard .footer-options {

text-align: right;

}

  

#book-appointment-wizard #select-language {

display: inline-block;

}

  

#book-appointment-wizard .backend-link {

display: inline-block;

min-width: 120px;

padding: 5px;

margin: 5px 0;

}

}

  

/* BOOK SUCCESS & MESSAGE

------------------------------------------------------------------------- */

  

#message-frame,

#success-frame {

background: var(--bs-body-bg);

text-align: center;

height: auto;

border: none;

padding: 35px;

}

  

#message-frame .alert,

#success-frame .alert {

margin-top: 20px;

}

  

#message-frame #message-icon,

#success-frame #success-icon {

margin-top: 20px;

margin-right: 20px;

width: 64px;

display: block;

margin: auto;

float: none !important;

}

  

#success-frame .btn {

margin-bottom: 10px;

width: 80%;

max-width: 300px;

}

  

@media (min-width: 768px) {

#message-frame,

#success-frame {

height: 100%;

}

}

  

/* CANCEL APPOINTMENT

------------------------------------------------------------------------- */

  

.booking-header-bar {

padding: 15px 0;

margin: 0;

background: #f3f2e7;

border-bottom: 1px solid #e4e1c9;

text-align: center;

}

  

.ui-dialog .ui-dialog-title {

font-size: 1.2em;

}

  

@media (min-width: 768px) {

.booking-header-bar {

padding: 15px 0;

margin: 0;

background: #f3f2e7;

border-bottom: 1px solid #e4e1c9;

text-align: left;

}

}
```

```css general.scss
/* ----------------------------------------------------------------------------

* Easy!Appointments - Online Appointment Scheduler

*

* @package EasyAppointments

* @author A.Tselegidis <alextselegidis@gmail.com>

* @copyright Copyright (c) Alex Tselegidis

* @license https://opensource.org/licenses/GPL-3.0 - GPLv3

* @link https://easyappointments.org

* @since v1.5.0

* ---------------------------------------------------------------------------- */

  

html {

height: 100%;

}

  

select {

-webkit-appearance: none;

}

  

@-moz-document url-prefix() {

body .checkbox input[type='checkbox'] {

float: left;

}

}

  

body .ui-widget {

font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, 'Noto Sans', sans-serif,

'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';

font-size: 1.1em;

}

  

body .ui-widget-overlay {

background: #000 50% 50% repeat-x;

opacity: 0.5;

filter: Alpha(Opacity=50);

}

  

body .ui-dialog .ui-dialog-titlebar-close {

display: none;

}

  

body .ui-draggable .ui-dialog-titlebar {

background: #429a82;

color: #fff;

font-size: 1.2em;

font-weight: lighter;

padding: 12px 10px;

margin-bottom: 10px;

border: none;

border-top-left-radius: 0.25rem;

border-top-right-radius: 0.25rem;

border-bottom-left-radius: 0;

border-bottom-right-radius: 0;

}

  

body .ui-dialog {

padding: 0;

z-index: 2000;

border: none !important;

box-shadow: 0 0 10px #333;

}

  

body .ui-dialog .ui-dialog-buttonpane {

padding: 0.3em 1em 0.3em 0.4em;

border: none;

}

  

body .ui-button .ui-icon,

body .ui-button:hover .ui-icon {

background-image: url('../ext/jquery-ui/images/ui-icons_222222_256x240.png');

}

  

body .ui-dialog #error-technical {

max-width: 500px;

}

  

body .ui-widget.ui-widget-content {

border: 1px solid #429a82;

padding: 0;

}

  

body .ui-dialog-buttons {

border-radius: 0.25rem;

}

  

body #ui-datepicker-div {

margin-top: 5px;

z-index: 1100 !important;

}

  

body .ui-datepicker {

width: auto;

max-width: 288px;

}

  

body .ui-datepicker .ui-widget-header {

border: none;

background: #429a82;

border-radius: 0;

}

  

body .ui-datepicker .ui-widget-header .ui-icon {

background-image: url('../vendor/jquery-ui-dist/images/ui-icons_ffffff_256x240.png');

}

  

body .ui-datepicker .ui-datepicker-title {

color: white;

padding: 8px 5px;

}

  

body .ui-datepicker th {

background: #429a82;

color: #fff;

}

  

body .ui-datepicker tbody tr:first-child td {

margin-top: 5px;

}

  

body .ui-datepicker td a,

body .ui-datepicker td span {

border: none !important;

background: none !important;

color: #1a865f !important;

text-align: center !important;

width: 32px;

height: 32px;

line-height: 2;

}

  

html body .ui-datepicker td a.ui-state-active {

color: #fff !important;

font-weight: bold !important;

background: #429a82 !important;

border-radius: 50px;

width: 24px;

height: 24px;

line-height: 1.2;

margin: 4px;

}

  

body .ui-datepicker td a.ui-state-highlight {

background: #80e3ad !important;

border-radius: 67px;

color: #fff !important;

width: 24px;

height: 24px;

line-height: 1.2;

margin: 4px;

}

  

body .ui-datepicker .ui-datepicker-prev-hover {

top: 2px !important;

left: 2px !important;

background: #80e1ac;

border-color: #80e1ac;

border-radius: 0;

cursor: pointer;

}

  

body .ui-datepicker .ui-datepicker-next-hover {

top: 2px !important;

right: 2px !important;

background: #80e1ac;

border-color: #80e1ac;

border-radius: 0;

cursor: pointer;

}

  

body .ui-datepicker .ui-slider-handle {

border-radius: 0;

border-color: #429a82;

background-color: #429a82;

}

  

body .ui-priority-primary,

body .ui-widget-content .ui-priority-primary,

body .ui-widget-header .ui-priority-primary {

font-weight: normal;

}

  

body .ui-widget input,

.ui-widget select,

body .ui-widget textarea,

body .ui-widget button {

font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, 'Noto Sans', sans-serif,

'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';

font-size: 1rem;

}

  

body .ui-datepicker .ui-datepicker-buttonpane button {

padding: 6px 16px;

}

  

.breaks tr:hover td {

background: #ffffc2 !important;

}

  

.working-plan td {

vertical-align: middle;

}

  

.breaks td {

vertical-align: middle;

}

  

li.language {

cursor: pointer;

}

  

li.language:hover {

color: #005580;

}

  

#select-language {

cursor: pointer;

display: inline-block;

padding: 5px;

}

  

#language-list {

list-style: none;

padding-left: 0;

max-height: 500px;

overflow-y: auto;

}

  

/* JQUERY UI DATETIME PICKER ADDON

------------------------------------------------------------------------- */

  

.ui-timepicker-div .ui-widget-header {

margin-bottom: 8px;

}

  

.ui-timepicker-div dl {

text-align: left;

}

  

.ui-timepicker-div dl dt {

float: left;

clear: left;

padding: 0 0 0 5px;

}

  

.ui-timepicker-div dl dd {

margin: 0 10px 10px 40%;

}

  

.ui-timepicker-div dl dd.ui_tpicker_time {

margin-bottom: 4px;

}

  

.ui-timepicker-div dl dd.ui_tpicker_hour,

.ui-timepicker-div dl dd.ui_tpicker_minute {

padding-top: 8px;

}

  

.ui-timepicker-div td {

font-size: 90%;

}

  

.ui-tpicker-grid-label {

background: none;

border: none;

margin: 0;

padding: 0;

}

  

.ui-timepicker-div .ui_tpicker_unit_hide {

display: none;

}

  

.ui-timepicker-div .ui_tpicker_time .ui_tpicker_time_input {

background: none;

color: inherit;

border: none;

outline: none;

width: 95%;

}

  

.ui-timepicker-div .ui_tpicker_time .ui_tpicker_time_input:focus {

border-bottom-color: #aaa;

}

  

.ui-timepicker-rtl {

direction: rtl;

}

  

.ui-timepicker-rtl dl {

text-align: right;

padding: 0 5px 0 0;

}

  

.ui-timepicker-rtl dl dt {

float: right;

clear: right;

}

  

.ui-timepicker-rtl dl dd {

margin: 0 40% 10px 10px;

}

  

/* Shortened version style */

.ui-timepicker-div.ui-timepicker-oneLine {

padding-right: 2px;

}

  

.ui-timepicker-div.ui-timepicker-oneLine .ui_tpicker_time,

.ui-timepicker-div.ui-timepicker-oneLine dt {

display: none;

}

  

.ui-timepicker-div.ui-timepicker-oneLine .ui_tpicker_time_label {

display: block;

padding-top: 2px;

}

  

.ui-timepicker-div.ui-timepicker-oneLine dl {

text-align: right;

}

  

.ui-timepicker-div.ui-timepicker-oneLine dl dd,

.ui-timepicker-div.ui-timepicker-oneLine dl dd>div {

display: inline-block;

margin: 0;

}

  

.ui-timepicker-div.ui-timepicker-oneLine dl dd.ui_tpicker_minute:before,

.ui-timepicker-div.ui-timepicker-oneLine dl dd.ui_tpicker_second:before {

content: ':';

display: inline-block;

}

  

.ui-timepicker-div.ui-timepicker-oneLine dl dd.ui_tpicker_millisec:before,

.ui-timepicker-div.ui-timepicker-oneLine dl dd.ui_tpicker_microsec:before {

content: '.';

display: inline-block;

}

  

.ui-timepicker-div.ui-timepicker-oneLine .ui_tpicker_unit_hide,

.ui-timepicker-div.ui-timepicker-oneLine .ui_tpicker_unit_hide:before {

display: none;

}

  

/* LOADING SPINNER

------------------------------------------------------------------------- */

  

.is-loading {

position: relative;

}

  

.is-loading:before,

.is-loading:after {

content: '';

position: absolute;

top: 50%;

left: 50%;

}

  

.animation:after {

width: 60px;

height: 60px;

margin: -25px 0 0 -25px;

  

border: 5px solid rgba(0, 0, 0, 0.4);

border-radius: 50px;

}

  

.animation:after {

border-bottom-color: transparent;

animation: spin 1s infinite linear;

}

  

@keyframes spin {

from {

transform: rotate(0deg);

}

  

to {

transform: rotate(360deg);

}

}

  

@keyframes spin-reverse {

from {

transform: rotate(0deg);

}

  

to {

transform: rotate(-360deg);

}

}

  

.any-element {

width: 60px;

height: 60px;

position: fixed;

left: 50vw;

top: 50vh;

margin-left: -30px;

margin-bottom: -30px;

}

  

#message-box pre,

#message-box .card {

max-height: 250px;

max-width: 500px;

}

  

body .popover {

max-width: 430px;

}

  

body .popover-body strong {

min-width: 90px;

display: inline-block;

}

  

body .popover-body button {

font-size: 1em;

box-sizing: border-box;

margin: 0;

height: 2.1em;

padding: 0 0.6em;

}

  

body .popover-body a {

margin-right: 5px;

}

  

.has-error .control-label,

.has-error label {

color: #dc3545;

}

  

.has-error .form-control,

.has-error .form-select {

border-color: #dc3545;

}

  

body .clearfix {

clear: both;

}

  

.cc-revoke,

.cc-window {

z-index: 999 !important;

}

  

.flatpickr-wrapper {

width: 100%

}

  

.flatpickr-calendar {

box-shadow: none

}

  

.flatpickr-calendar .flatpickr-monthDropdown-months:hover {

background: rgba(0, 0, 0, .05) !important

}

  

.flatpickr-calendar .flatpickr-months {

padding: 10px 0

}

  

.flatpickr-calendar .flatpickr-current-month {

padding: 3px

}

  

.flatpickr-calendar .flatpickr-innerContainer {

border-bottom-left-radius: 3px;

border-bottom-right-radius: 3px

}

  

.flatpickr-calendar .dayContainer {

padding: 10px 0

}

  

.flatpickr-calendar .flatpickr-current-month .flatpickr-monthDropdown-months,

.flatpickr-calendar .flatpickr-current-month input.cur-year[disabled],

.flatpickr-calendar .flatpickr-current-month input.cur-year[disabled]:hover,

.flatpickr-calendar .flatpickr-months .flatpickr-month,

.flatpickr-calendar .flatpickr-weekdays,

.flatpickr-calendar span.flatpickr-weekday {

color: #000;

-webkit-appearance: none

}

  

.flatpickr-calendar .flatpickr-current-month .flatpickr-monthDropdown-months,

.flatpickr-calendar .flatpickr-months .flatpickr-month,

.flatpickr-calendar .flatpickr-weekdays,

.flatpickr-calendar span.flatpickr-weekday {

background: #fff

}

  

.flatpickr-calendar .flatpickr-months .flatpickr-next-month svg path,

.flatpickr-calendar .flatpickr-months .flatpickr-prev-month svg path {

fill: #000

}

  

.flatpickr-calendar .flatpickr-day.endRange,

.flatpickr-calendar .flatpickr-day.endRange.inRange,

.flatpickr-calendar .flatpickr-day.endRange.nextMonthDay,

.flatpickr-calendar .flatpickr-day.endRange.prevMonthDay,

.flatpickr-calendar .flatpickr-day.endRange:focus,

.flatpickr-calendar .flatpickr-day.endRange:hover,

.flatpickr-calendar .flatpickr-day.selected,

.flatpickr-calendar .flatpickr-day.selected.inRange,

.flatpickr-calendar .flatpickr-day.selected.nextMonthDay,

.flatpickr-calendar .flatpickr-day.selected.prevMonthDay,

.flatpickr-calendar .flatpickr-day.selected:focus,

.flatpickr-calendar .flatpickr-day.selected:hover,

.flatpickr-calendar .flatpickr-day.startRange,

.flatpickr-calendar .flatpickr-day.startRange.inRange,

.flatpickr-calendar .flatpickr-day.startRange.nextMonthDay,

.flatpickr-calendar .flatpickr-day.startRange.prevMonthDay,

.flatpickr-calendar .flatpickr-day.startRange:focus,

.flatpickr-calendar .flatpickr-day.startRange:hover {

background: #11ade4;

border-color: #11ade4;

color: #fff

}

  

.flatpickr-calendar .flatpickr-day.nextMonthDay,

.flatpickr-calendar .flatpickr-day.prevMonthDay {

height: 0;

width: 0;

visibility: hidden

}

  

.flatpickr-days,

.flatpickr-innerContainer {

border: 0

}

  

.flatpickr-wrapper {

box-shadow: 0 4px 16px rgba(0, 0, 0, .1);

border-radius: 8px

}
```