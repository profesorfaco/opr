### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 11 → 15/05/2026

# Diseño y programación: Definición de la propuesta

### Teoría (para la casa)

Aprovechando lo ingresado en el foro hasta el miércoles, podemos partir con el siguiente código. Es fundamental notar, al final del script, el uso de `document.getElementById("filtro-especie").addEventListener("change", function () {…}`.

Este método permite que la página "reaccione" inmediatamente cuando el usuario selecciona una opción distinta en el menú desplegable.

```

<!doctype html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Aves de Chile</title>
        <style>
            @import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@200..900&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap");

            *,
            *::before,
            *::after {
                box-sizing: border-box;
                margin: 0;
                padding: 0;
            }

            :root {
                --texto: #000;
                --fondo: #eee;
                --blanco: #fff;
                --fuente: "Inconsolata", monospace;
                --otrafuente: "Roboto", sans-serif;
            }

            body {
                font-family: var(--fuente);
                background: var(--fondo);
            }
            svg#escondido {
                display: none;
            }

            div#contenedor {
                width: 90%;
                max-width: 580px;
                margin: 1rem auto;
                box-shadow: 0 0 3px rgba(200, 200, 200, 0.5);
                padding: 2rem;
                background: var(--blanco);
            }

            h1 {
                font-family: var(--otrafuente);
                text-align: left center;
                font-size: calc(1rem + 2vw + 2vh);
                margin: 3vw auto;
                padding-left:calc(2rem + 2vw + 2vh);
                background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" width="800px" height="800px" viewBox="-3.89 0 62.445 62.445"><g id="Group_5854" data-name="Group 5854" transform="translate(-1070.472 -1197.651)"><g id="Group_5852" data-name="Group 5852"><g id="Group_5800" data-name="Group 5800"><g id="Group_5799" data-name="Group 5799"><g id="Group_5798" data-name="Group 5798"><path id="Path_2121" data-name="Path 2121" d="M1115.252,1233.129c-.458-.254-.82-.446-1.052-.567.492.531.825.91,1,1.109C1115.214,1233.489,1115.238,1233.315,1115.252,1233.129Z" fill="%23b3b347"/></g></g></g><g id="Group_5803" data-name="Group 5803"><g id="Group_5802" data-name="Group 5802"><g id="Group_5801" data-name="Group 5801"><path id="Path_2122" data-name="Path 2122" d="M1071.435,1208.359l2.8,2.8-1.8.9a.611.611,0,0,0-.023,1.081l7.306,4.059,2.614-5.229-10.094-4.751A.709.709,0,0,0,1071.435,1208.359Z" fill="%23333"/></g></g></g><g id="Group_5806" data-name="Group 5806"><g id="Group_5805" data-name="Group 5805"><g id="Group_5804" data-name="Group 5804"><path id="Path_2123" data-name="Path 2123" d="M1123.84,1243.755s1.589-2.769-1.418-5.669a37.576,37.576,0,0,0-7.17-4.957c-.014.186-.038.36-.055.542a20.656,20.656,0,0,1-2.72,8.667,16.7,16.7,0,0,1-3.581,4.252h10.692l1.417-2.835Z" fill="%23333"/></g></g></g><g id="Group_5809" data-name="Group 5809"><g id="Group_5808" data-name="Group 5808"><g id="Group_5807" data-name="Group 5807"><path id="Path_2124" data-name="Path 2124" d="M1121.005,1243.755l-1.417,2.835s2.176,2.573,4.252,2.834a7.611,7.611,0,0,0,0-5.669Z" fill="%23b3b3b3"/></g></g></g><g id="Group_5812" data-name="Group 5812"><g id="Group_5811" data-name="Group 5811"><g id="Group_5810" data-name="Group 5810"><circle id="Ellipse_160" data-name="Ellipse 160" cx="1.417" cy="1.417" r="1.417" transform="translate(1118.17 1239.503)" fill="%23b3b347"/></g></g></g><g id="Group_5815" data-name="Group 5815"><g id="Group_5814" data-name="Group 5814"><g id="Group_5813" data-name="Group 5813"><path id="Path_2125" data-name="Path 2125" d="M1105.415,1229.582v11.428a4.987,4.987,0,0,0,2.834,1.328v-8.5Z" fill="%23333"/></g></g></g><g id="Group_5818" data-name="Group 5818"><g id="Group_5817" data-name="Group 5817"><g id="Group_5816" data-name="Group 5816"><path id="Path_2126" data-name="Path 2126" d="M1106.191,1241.574a5.84,5.84,0,0,0,1.062.557l.065.023c.083.03.165.057.246.079l.092.025c.074.018.147.033.22.045l.086.014a2.189,2.189,0,0,0,.287.021v-8.5l-2.834-4.252v11.428q.4.315.774.562Z" fill="%23333"/></g></g></g><g id="Group_5821" data-name="Group 5821"><g id="Group_5820" data-name="Group 5820"><g id="Group_5819" data-name="Group 5819"><path id="Path_2127" data-name="Path 2127" d="M1099.61,1219.862l.135.1c.137.1.268.2.4.3.255.186.509.373.758.558.18.134.355.267.532.4.249.188.5.376.74.562.168.129.332.257.5.385.242.188.485.376.72.562.155.122.3.242.457.363.236.189.473.378.7.564l.419.344c.23.188.46.376.683.562.13.108.255.214.383.322.222.186.444.373.659.556.122.1.238.206.358.309.211.182.423.364.626.542l.327.289c.2.179.406.358.6.533l.289.261c.2.178.393.355.58.527.09.082.173.161.26.242.185.17.371.342.546.507.089.082.171.161.256.242l.494.469c.084.08.161.156.243.235.151.146.3.293.446.434.08.078.152.15.229.226l.4.4c.075.076.142.145.215.218l.353.357.268.276c.081.085.167.173.244.253.161.167.311.326.451.475-.185-.907-1.517-5.116-10.893-12.568h-3.663C1099.427,1219.728,1099.516,1219.8,1099.61,1219.862Z" fill="%23b3b347"/></g></g></g><g id="Group_5824" data-name="Group 5824"><g id="Group_5823" data-name="Group 5823"><g id="Group_5822" data-name="Group 5822"><path id="Path_2128" data-name="Path 2128" d="M1104.974,1223.994l-.419-.344c-.23-.186-.467-.375-.7-.564-.152-.121-.3-.241-.457-.363-.235-.186-.478-.374-.72-.562-.165-.128-.329-.256-.5-.385-.242-.186-.491-.374-.74-.562-.177-.133-.352-.266-.532-.4-.248-.185-.5-.372-.758-.558l-.4-.295v8.2l2.835,4.252v5.791l.131.147c.176.2.35.394.523.581.072.078.144.153.216.229q.24.255.477.493c.065.065.129.13.194.193q.267.261.526.5l.121.111c.219.2.435.38.647.549v-16.654C1105.268,1224.236,1105.123,1224.115,1104.974,1223.994Z" fill="%23ffff40"/></g></g></g><g id="Group_5827" data-name="Group 5827"><g id="Group_5826" data-name="Group 5826"><g id="Group_5825" data-name="Group 5825"><path id="Path_2129" data-name="Path 2129" d="M1114.2,1232.562c-.178-.093-.282-.145-.282-.145a1.579,1.579,0,0,0-.029-.188c-.14-.149-.291-.308-.451-.475-.077-.08-.163-.168-.244-.253l-.268-.276-.353-.357c-.073-.073-.14-.142-.215-.218l-.4-.4c-.077-.076-.149-.148-.229-.226l-.446-.434c-.082-.079-.159-.155-.243-.235l-.494-.469c-.085-.081-.167-.16-.256-.242-.175-.165-.361-.337-.546-.507-.087-.081-.17-.16-.26-.242-.187-.172-.384-.349-.58-.527l-.289-.261c-.195-.174-.4-.354-.6-.533l-.327-.289c-.2-.178-.415-.36-.626-.542-.12-.1-.236-.205-.358-.309-.215-.183-.437-.37-.659-.556-.128-.108-.253-.214-.383-.322l-.242-.2v5.226l2.834,4.252v8.5h4.228a20.656,20.656,0,0,0,2.72-8.667C1115.025,1233.472,1114.692,1233.093,1114.2,1232.562Z" fill="%23b3b347"/></g></g></g><g id="Group_5830" data-name="Group 5830"><g id="Group_5829" data-name="Group 5829"><g id="Group_5828" data-name="Group 5828"><path id="Path_2130" data-name="Path 2130" d="M1092.659,1238.125v21.221h2.834v-17.932A29.144,29.144,0,0,1,1092.659,1238.125Z" fill="%23be8a66"/></g></g></g><g id="Group_5833" data-name="Group 5833"><g id="Group_5832" data-name="Group 5832"><g id="Group_5831" data-name="Group 5831"><path id="Path_2131" data-name="Path 2131" d="M1095.493,1198.4h-2.834v13.97q1.485.95,2.834,1.852Z" fill="%23be8a66"/></g></g></g><g id="Group_5836" data-name="Group 5836"><g id="Group_5835" data-name="Group 5835"><g id="Group_5834" data-name="Group 5834"><path id="Path_2132" data-name="Path 2132" d="M1095.493,1214.223q-1.35-.9-2.834-1.852-2-1.275-4.252-2.632l3.066,4.74c.4.243.792.487,1.186.731.356.22.716.44,1.064.661.144.091.281.182.424.274.453.29.907.58,1.346.87l.271.181c.224.148.438.3.659.444.434.293.868.585,1.287.877.248.172.487.342.73.514.3.21.6.421.893.63H1103C1100.916,1218.008,1098.439,1216.195,1095.493,1214.223Z" fill="%23333"/></g></g></g><g id="Group_5839" data-name="Group 5839"><g id="Group_5838" data-name="Group 5838"><g id="Group_5837" data-name="Group 5837"><path id="Path_2133" data-name="Path 2133" d="M1108.249,1242.338a2.189,2.189,0,0,1-.287-.021l-.086-.014c-.073-.012-.146-.027-.22-.045l-.092-.025c-.081-.022-.163-.049-.246-.079l-.065-.023a5.84,5.84,0,0,1-1.062-.557h0q-.379-.248-.775-.563v0c-.212-.169-.428-.355-.647-.551l-.121-.111c-.173-.159-.348-.324-.526-.5-.065-.063-.129-.128-.194-.193q-.237-.238-.477-.493c-.072-.076-.144-.151-.216-.229-.173-.187-.347-.382-.523-.581-.044-.05-.087-.095-.131-.146l-.03-.035c-.252-.29-.508-.593-.765-.9-.066-.08-.132-.163-.2-.244q-.308-.378-.618-.775l-.2-.259c-.264-.342-.529-.69-.8-1.048l-.061-.083q-.374-.5-.75-1.03c-.069-.095-.137-.191-.205-.287q-.352-.493-.7-1l-.111-.159q-.414-.6-.827-1.215c-.046-.067-.091-.136-.137-.2-.235-.35-.468-.7-.7-1.059l-.166-.253q-.409-.627-.815-1.261c-.976-1.53-1.929-3.081-2.834-4.593-1.891-3.158-3.572-6.143-4.822-8.421-.213-.388-.417-.76-.6-1.1l-4.9-2.306-2.614,5.229,4.437,2.465s2.613,10.569,8.5,18.464a29.144,29.144,0,0,0,2.834,3.289c3.082,3.053,6.841,5.176,11.339,5.176h2.064a16.7,16.7,0,0,0,3.581-4.252Z" fill="%23ffff40"/></g></g></g><g id="Group_5842" data-name="Group 5842"><g id="Group_5841" data-name="Group 5841"><g id="Group_5840" data-name="Group 5840"><path id="Path_2134" data-name="Path 2134" d="M1092.659,1216.354l-1.09-1.816c-.033-.02-.063-.04-.1-.059-1.866-1.124-3.829-2.238-5.9-3.322,0,0,.62,1.2,1.662,3.116.186.344.39.716.6,1.1,1.25,2.278,2.931,5.263,4.822,8.42.9,1.513,1.858,3.063,2.834,4.593v-7.312Z" fill="%23333"/></g></g></g><g id="Group_5845" data-name="Group 5845"><g id="Group_5844" data-name="Group 5844"><g id="Group_5843" data-name="Group 5843"><path id="Path_2135" data-name="Path 2135" d="M1099.745,1228.165v-8.2l-.135-.1c-.381-.275-.776-.553-1.17-.831-.243-.172-.482-.342-.73-.514-.419-.292-.853-.584-1.287-.877-.22-.148-.435-.3-.659-.444-.088-.059-.182-.118-.271-.177q-.662-.437-1.346-.874c-.143-.092-.28-.183-.424-.274-.348-.221-.708-.441-1.064-.661v0c-.364-.225-.718-.45-1.09-.674l1.09,1.816,2.834,4.724v7.312h0q.4.634.815,1.262l.166.253c.233.355.467.709.7,1.059.045.068.091.137.137.2q.413.615.827,1.215l.111.159q.352.508.7,1c.068.1.136.192.205.287q.375.525.75,1.03l.061.083c.267.358.532.706.8,1.048l.2.259q.311.4.618.775l.2.244c.257.312.513.615.765.9l.03.034v-5.791Z" fill="%23ffff40"/></g></g></g><g id="Group_5848" data-name="Group 5848"><g id="Group_5847" data-name="Group 5847"><g id="Group_5846" data-name="Group 5846"><path id="Path_2136" data-name="Path 2136" d="M1106.191,1241.574a5.84,5.84,0,0,0,1.062.557l.065.023c.083.03.165.057.246.079l.092.025c.074.018.147.033.22.045l.086.014a2.189,2.189,0,0,0,.287.021v-8.5l-2.834-4.252v11.428q.4.315.774.562Z" fill="none"/></g></g></g><g id="Group_5851" data-name="Group 5851"><g id="Group_5850" data-name="Group 5850"><g id="Group_5849" data-name="Group 5849"><path id="Path_2137" data-name="Path 2137" d="M1109.48,1227.9c-.187-.172-.384-.349-.58-.527C1109.1,1227.546,1109.293,1227.723,1109.48,1227.9Z" fill="none"/></g></g></g></g><g id="Group_5853" data-name="Group 5853"><path id="Path_2138" data-name="Path 2138" d="M1124.652,1243.8c.552-1.291.769-3.859-1.709-6.249a38.432,38.432,0,0,0-7.327-5.073.729.729,0,0,0-.527-.052l-.339-.369a.785.785,0,0,0-.163-.129c-.329-1.348-2.06-5.644-11.124-12.849-2.128-1.691-4.56-3.456-7.22-5.247V1198.4a.75.75,0,0,0-1.5,0v14.426q-.662-.435-1.335-.866V1198.4a.75.75,0,0,0-1.5,0v12.613q-1.53-.96-3.115-1.918a.75.75,0,0,0-1.016,1.051l1.361,2.1c-1.076-.61-2.152-1.2-3.218-1.759a.75.75,0,0,0-1.014,1.01c0,.007.219.421.593,1.126l-2.847-1.34-10.095-4.75a1.458,1.458,0,0,0-1.652,2.351h0l2.062,2.062-.867.434a1.362,1.362,0,0,0-.052,2.408l7.305,4.059,4.156,2.308c.488,1.845,3.092,10.983,8.4,18.2v9.716c-.06.043-.123.082-.181.13a3.36,3.36,0,0,0-1.236,2.6.75.75,0,0,0,.723.776h.027a.747.747,0,0,0,.667-.418v8.172a.75.75,0,0,0,1.5,0V1248.98a5.186,5.186,0,0,1,1.335-.292v10.658a.75.75,0,0,0,1.5,0v-8.112a4.331,4.331,0,0,0,1.417-3.24.616.616,0,0,0-.017-.072.724.724,0,0,0-.044-.178.656.656,0,0,0-.018-.073l-1.338-2.676v-1.875a16.059,16.059,0,0,0,10.589,4.22h12.421c.653.705,2.556,2.584,4.493,2.829.031,0,.063.005.094.005a.75.75,0,0,0,.68-.434A8.362,8.362,0,0,0,1124.652,1243.8Zm-53.217-35.436.526-.536,0,.007Zm42.662,27.592a20.851,20.851,0,0,1-.528,2.074c-.047.152-.111.293-.161.442-.173.511-.354,1.017-.565,1.5-.1.23-.22.444-.329.668-.157.323-.317.643-.492.952H1109v-7.754a.752.752,0,0,0-.126-.416l-2.709-4.063v-3.39l.048.04,3.02,2.683c.183.169.367.339.539.5l.256.243c.166.156.332.313.487.462l2.383,2.379c.1.107.2.205.29.305a.75.75,0,0,0,.393.508l.159.082c.279.3.5.549.666.737-.055.49-.13.968-.213,1.441C1114.158,1235.546,1114.137,1235.754,1114.1,1235.951Zm-7.067,5.248c-.109-.06-.222-.127-.337-.2-.036-.023-.07-.043-.108-.068-.134-.087-.279-.2-.421-.3v-8.569l1.335,2v7.359c-.12-.047-.247-.106-.376-.172Zm-9.231-10.652q-.351-.523-.7-1.052l-.165-.253q-.348-.534-.693-1.072v-7.092a.75.75,0,0,0-.107-.386l-2.322-3.869.082.052c.4.257.8.513,1.183.77l.925.617c.431.291.862.581,1.279.871.163.113.322.226.481.338l.337.239c.3.212.6.424.894.634v7.821a.751.751,0,0,0,.126.416l2.709,4.063v3.483c-.09-.113-.179-.223-.27-.338l-.2-.258c-.262-.337-.523-.681-.793-1.044l-.054-.074c-.248-.333-.5-.675-.744-1.02l-.2-.285c-.232-.327-.465-.657-.7-.995l-.109-.156c-.275-.4-.549-.8-.821-1.205Zm5.986,7.879c-.149-.161-.3-.331-.455-.505v-5.5a.751.751,0,0,0-.126-.416l-2.709-4.063v-6.494l.492.37c.247.186.494.373.734.557l.561.435c.218.169.436.338.649.506l.453.361c.235.187.47.374.7.561l.563.461.018.015v14.623l-.017-.016-.189-.188c-.153-.154-.307-.314-.463-.478Zm6.715-10.608-.25-.231-.262-.244-.462-.42-.028-.024-.1-.087-.29-.262c-.008-.007-.019-.009-.027-.016l-1.9-1.67c-.216-.185-.44-.373-.664-.561l-.385-.323-.242-.2,0,0h0l-.047-.039-.311-.256-.084-.069h0l-.421-.345c-.232-.188-.471-.378-.709-.568l-.231-.184-.227-.181c-.216-.171-.437-.342-.659-.514l-.567-.44c-.245-.188-.5-.377-.746-.565l-.272-.2h1.117A50.993,50.993,0,0,1,1110.5,1227.818ZM1092.255,1213c.955.61,1.9,1.23,2.821,1.844,2.06,1.378,3.978,2.74,5.728,4.064h-1.23c-.134-.095-.269-.19-.405-.284l-.537-.379c-.164-.116-.327-.232-.494-.348-.394-.272-.8-.546-1.206-.821l-.017-.011-.073-.05-.113-.076-.822-.553c-.436-.287-.886-.575-1.356-.876l-.427-.276c-.262-.166-.532-.333-.8-.5l-.607-.376c-.234-.145-.468-.291-.707-.436l-1.18-1.823Q1091.551,1212.555,1092.255,1213Zm-1.233,2.079.782,1.306.211.351,2.728,4.547v4.5q-.71-1.149-1.441-2.371c-1.587-2.652-3.2-5.476-4.808-8.4-.212-.386-.415-.757-.6-1.1s-.347-.641-.5-.927Q1089.194,1213.984,1091.022,1215.082Zm-16.259-4.455-2.63-2.631,9.185,4.322-1.921,3.842-6.391-3.551,1.563-.781a.75.75,0,0,0,.194-1.2Zm19.054,30.086c.131.147.262.288.393.43l-.664.665a.747.747,0,0,0-.138.189v-1.73c.015.017.03.031.044.048C1093.573,1240.455,1093.7,1240.577,1093.817,1240.713Zm-.409,6.687v-4.72l1.335,2.669v1.832A7.511,7.511,0,0,0,1093.408,1247.4Zm2.911-6.245,1.122-1.122a.75.75,0,0,0-1.061-1.06l-1.106,1.106a29.278,29.278,0,0,1-2.014-2.4c-5.729-7.677-8.352-18.091-8.377-18.2a.749.749,0,0,0-.364-.476l-3.809-2.116.984-1.969.982-1.963,4.016,1.89c.154.283.318.582.487.89,1.615,2.942,3.242,5.784,4.836,8.446.98,1.636,1.937,3.188,2.846,4.612q.406.636.819,1.267l.166.254q.353.537.706,1.065l.137.206q.415.618.832,1.222l.113.161q.354.512.708,1.008l.208.29c.253.352.505.7.764,1.049l.054.073c.269.363.538.715.806,1.061l.2.261c.21.269.42.53.626.784l.2.249c.261.318.521.626.807.955l.135.151c.18.2.359.4.534.592l.223.238c.165.174.328.344.491.507l.2.2c.184.18.365.351.549.519l.122.113.025.021c.221.2.442.388.656.559l.039.029c.265.209.526.4.777.562l.019.013.042.024c.051.034.1.058.151.089.207.126.408.237.6.331.082.039.163.077.244.111.049.021.1.05.15.069l.087.031c.1.037.2.069.327.1l.087.024h0c.026.006.052.009.078.015.069.015.136.03.221.045l.088.014a2.983,2.983,0,0,0,.384.027h2.839c-.02.029-.041.06-.062.088-.193.268-.387.525-.579.761-.023.029-.047.055-.07.083q-.264.32-.52.6c-.047.052-.094.1-.141.154-.377.4-.734.745-1.052,1.024l-.047.042h-1.785C1103.093,1245.84,1099.56,1244.255,1096.319,1241.155Zm14.59,4.536c.114-.123.227-.249.343-.383.072-.083.143-.168.216-.255.112-.135.225-.276.339-.421.073-.093.144-.185.217-.282.123-.162.244-.333.366-.507.063-.09.125-.175.188-.268.183-.272.365-.554.543-.853a19.169,19.169,0,0,0,.937-1.794c.022-.049.047-.095.069-.143.267-.594.5-1.209.715-1.839.026-.079.056-.157.082-.237.2-.619.371-1.256.52-1.907.022-.1.046-.2.067-.3q.209-.974.338-1.995c.007-.056.021-.108.028-.163a33.745,33.745,0,0,1,6.025,4.28c1.941,1.872,1.686,3.627,1.442,4.379h-2.339a.751.751,0,0,0-.671.415l-1.21,2.42h-8.348C1110.82,1245.794,1110.866,1245.739,1110.909,1245.691Zm12.448,2.846a8.659,8.659,0,0,1-2.869-2.071l.981-1.961h1.848A6.982,6.982,0,0,1,1123.357,1248.537Z" fill="%231a1a1a"/><path id="Path_2139" data-name="Path 2139" d="M1119.588,1242.338a1.417,1.417,0,1,0-1.418-1.418A1.418,1.418,0,0,0,1119.588,1242.338Z" fill="%231a1a1a"/></g></g></svg>');
                background-repeat: no-repeat;
                background-size:calc(1.5rem + 2vw + 2vh);
            }

            h2 {
                font-family: var(--otrafuente);
                margin: 3rem 0 1rem 0;
            }

            /* === SELECT === */
            .filtro-wrapper {
                margin: 1.5rem 0 0.5rem 0;
            }

            .filtro-wrapper label {
                display: block;
                font-family: var(--otrafuente);
                font-size: 0.85rem;
                font-weight: 600;
                margin-bottom: 0.4rem;
                color: #444;
            }

            #filtro-especie {
                font-family: var(--fuente);
                font-size: 1rem;
                padding: 0.4rem 0.8rem;
                border: 1px solid silver;
                border-radius: 0;
                background: var(--blanco);
                color: var(--texto);
                cursor: pointer;
                appearance: none;
                -webkit-appearance: none;
                background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23333' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
                background-repeat: no-repeat;
                background-position: right 0.75rem center;
                padding-right: 2.2rem;
                min-width: 200px;
                transition: border-color ease 0.3s;
            }

            #filtro-especie:focus {
                outline: none;
                border-color: #333;
            }
            /* === FIN SELECT === */

            ol,
            ul {
                list-style-position: inside;
                list-style: none;
                width: 100%;
                margin: 1rem 0;
                border-top: 1px solid silver;
                font-family: var(--fuente);
            }

            ol li {
                border-bottom: 1px solid silver;
                padding: 0.5rem 0;
            }

            ol li:last-child {
                border-bottom: 3px solid silver;
            }

            ol li a {
                text-decoration: none;
                color: var(--texto);
                transition: all ease 0.5s;
            }

            ol li a:hover {
                letter-spacing: 0.1rem;
                transition: all ease 0.5s;
            }

            ol li a:nth-child(1) {
                display: inline-block;
                width: 50%;
            }

            ol li a[target="_blank"] {
                margin-left: 1rem;
            }

            .tiny {
                width: 2rem;
                height: auto;
                border-radius: 50% 50%;
                margin-right: 0.5rem;
            }

            /* POR DEFECTO, ESTA CLASE NO SE VE */
            .seccion-aves {
                display: none;
            }
            .seccion-aves.visible {
                display: block;
            }
        </style>
    </head>
    <body>
        <div id="contenedor">
            <h1>Aves de Chile</h1>
            <p>Chile es un país de características geográficas muy especiales. Una muestra de eso es la diversidad de ecosistemas que permiten la existencia de una rica biodiversidad, tanto nativa como endémica, en nuestro territorio.
            En esta entrada veremos específicamente las de aves chilenas, y su división según tipo de especie (nativa o endémica).</p>

            <p>Si quieres adentrarte y conocer más sobre las especies y la protección  animal, puedes visitar directamente el sitio de <a href="https://www.wwf.cl/?367212/Nativo-Endemico-y-Exotico-tres-importantes-conceptos-que-debes-conocer" target="_blank">World Wildlife Fund for Nature</a>.</p>

            <!-- SELECT FILTRO -->
            <div class="filtro-wrapper">
                <label for="filtro-especie">Mostrar aves:</label>
                <select id="filtro-especie">
                    <option value="">— Selecciona un grupo —</option>
                    <option value="endemica">Endémicas de Chile</option>
                    <option value="nativa">Nativas</option>
                </select>
            </div>
            <!-- FIN SELECT FILTRO -->

            <div id="seccion-endemica" class="seccion-aves">
                <h2>Endémica de Chile</h2>
                <p>Las especies endémicas son aquellas que habitan de manera natural en un solo espacio determinado, esto puede ser en un continente, un país, una isla o zona en particular y también en una región con límites administrativos o biogeográficos.</p>
                <ol id="dos"></ol>
            </div>

            <div id="seccion-nativa" class="seccion-aves">
                <h2>Nativas</h2>
                <p>Según la definición del Ministerio del Medio Ambiente (MMA), "las especies nativas corresponden a aquellas que viven de forma natural en Chile, es decir, que se cree que se originaron  o llegaron naturalmente al país, sin intervención humana". </p>
                <ol id="uno"></ol>
            </div>

        </div>

        <script>
            fetch("https://api.myjson.online/v1/records/b4cc6491-a885-4cf0-8760-c06ccd90e3ce")
                .then((respuesta) => {
                    if (!respuesta.ok) {
                        throw new Error("Error HTTP: " + respuesta.status);
                    }
                    return respuesta.json();
                })
                .then((datos) => {
                    var aves = datos.data;
                    console.log("Datos recibidos:", aves);
                    const primero = document.getElementById("uno");
                    const segundo = document.getElementById("dos");

                    aves.forEach((x) => {
                        if (x.info.species.value.includes("Nativa")) {
                            primero.innerHTML += `<li><img src="${x.image.url}" class="tiny"/>${x.names.spanish}</li>`;
                        }

                        if (x.info.species.value.includes("Endemica de Chile")) {
                            segundo.innerHTML += `<li><img src="${x.image.url}" class="tiny"/>${x.names.spanish}</li>`;
                        }
                    });
                })
                .catch((error) => {
                    console.error("Algo salió mal:", error);
                });

            // LO QUE SIGUE ES LO QUE PERMITE OPERAR AL SELECT DE IDENTIDAD filtro-especie

            document.getElementById("filtro-especie").addEventListener("change", function () {
                const valor = this.value;

                document.getElementById("seccion-endemica").classList.remove("visible");
                document.getElementById("seccion-nativa").classList.remove("visible");

                if (valor === "endemica") {
                    document.getElementById("seccion-endemica").classList.add("visible");
                } else if (valor === "nativa") {
                    document.getElementById("seccion-nativa").classList.add("visible");
                }
            });
        </script>
    </body>
</html>
```

Tal como se indica en [MDN](https://developer.mozilla.org/es/docs/Web/API/EventTarget/addEventListener), el `addEventListener()` escucha un evento específico (en este caso, `change`) sobre un objeto determinado (el `select`).

**Importante**: En este primer ejemplo, el JavaScript actúa como un "interruptor". Todas las aves ya están cargadas en el HTML, y el script solo decide qué "caja" (`div`) mostrar u ocultar aplicando o quitando la clase `.visible`.
 
- - - - 

#### Avanzando hacia una estructura dinámica

Podemos mejorar este proceso sin depender de elementos ocultos en el CSS. JavaScript puede ayudarnos a **generar contenido sobre la marcha** directamente en el [DOM](https://www.youtube.com/watch?v=4ILE0y58J00&t=101s). Esto es mucho más eficiente cuando trabajamos con grandes volúmenes de datos.

Observa cómo en este segundo ejemplo, el menú de selección no está escrito a mano, sino que se crea automáticamente analizando los datos de la API:

```
<!doctype html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Un fetch</title>
        <style>
            *,
            *::before,
            *::after {
                box-sizing: border-box;
                margin: 0;
                padding: 0;
            }

            :root {
                --texto: #000;
                --fondo: #eee;
                --blanco: #fff;
                --fuente: Helvetica, Arial, sans-serif;
            }

            body {
                font-family: var(--fuente);
                background: var(--fondo);
            }
            svg#escondido {
                display: none;
            }

            div#contenedor {
                width: 90%;
                max-width: 480px;
                margin: 1rem auto;
                box-shadow: 0 0 3px rgba(200, 200, 200, 0.5);
                padding: 1rem;
                background: var(--blanco);
            }

            h1 {
                text-align: left;
                font-size: calc(1rem + 2vw + 2vh);
                margin: 2vw auto;
            }

            h2 {
                margin: 3rem 0 1rem 0;
            }

            ol,
            ul {
                /* Quitamos el marcador nativo porque display:flex en los <li>
                   lo hace desaparecer. Los números los generamos nosotros con CSS. */
                list-style: none;
                counter-reset: numeracion-aves;
                width: 100%;
                margin: 1rem 0;
                border-top: 1px solid silver;
            }

            ol li {
                border-bottom: 1px solid silver;
                padding: 0.5rem 0;
            }

            ol li:last-child {
                border-bottom: 3px solid silver;
            }

            li {
                display: flex;
                flex-direction: row;
                align-items: center;
            }

            /* Cada <li> genera su propio número mediante un contador CSS */
            ol li::before {
                counter-increment: numeracion-aves;
                content: counter(numeracion-aves) ".";
                min-width: 2rem;
                font-weight: bold;
            }

            .tiny {
                width: 2rem;
                height: auto;
                border-radius: 50% 50%;
                margin-right: 0.5rem;
            }

            .filtro-wrapper{
                margin-top:1rem;
            }
        </style>
    </head>
    <body>
        <div id="contenedor">
            <h1>Aves de Chile</h1>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus malesuada mauris felis, sit amet ultrices felis finibus id. Praesent nec est venenatis, gravida lorem non, molestie odio. Sed a volutpat eros. Mauris at eros ultricies, pretium felis eget, bibendum ligula. Suspendisse vitae egestas risus. Vestibulum consectetur justo quis aliquet tincidunt.</p>

            <div class="filtro-wrapper">
                <label for="filtro-especie">Mostrar aves:</label>
                <select id="filtro-especie">
                    <option value="">— Selecciona un grupo —</option>
                </select>
            </div>

            <div id="resultado"></div>

        </div>

        <script>
            // Par de variables globales. Están encima de las funciones para que cualquiera de ellas pueda accederlas.
            let todasLasAves = [];
            const select = document.getElementById("filtro-especie");


            fetch("https://api.myjson.online/v1/records/b4cc6491-a885-4cf0-8760-c06ccd90e3ce")
                .then((respuesta) => {
                    if (!respuesta.ok) {
                        throw new Error("Error HTTP: " + respuesta.status);
                    }
                    return respuesta.json();
                })
                .then((datos) => {
                    todasLasAves = datos.data;
                    // Con lo que sigue, de cada ave extraemos el "value" del "order" en la "info".
                    // Con lo extraído, Set() elimina duplicados, y sort() los ordena alfabéticamente.
                    const ordenes = [...new Set(todasLasAves.map(x => x.info.order.value))].sort();
                    // Con cada valor único creamos un <option> y lo agregamos al <select>.
                    ordenes.forEach((o) => {
                        const option = document.createElement("option");
                        option.value = o;
                        option.textContent = o;
                        select.appendChild(option);
                    });
                })
                .catch((error) => {
                    console.error("Algo salió mal:", error);
                });

            // Esta función se llama cada vez que el usuario elige una opción del select; se recibe el valor seleccionado y se reconstruye el DOM desde cero.
            function renderizarAves(ordenSeleccionado) {
                const resultado = document.getElementById("resultado");
                // Limpiamos el contenedor antes de escribir el nuevo grupo. Sin limpiar, los resultados se acumularían uno tras otro.
                resultado.innerHTML = "";

                // Con opción vacía inicial, no hacemos nada más.
                if (!ordenSeleccionado) return;

                // El filter() recorre el arreglo completo y devuelve solo los elementos cuyo campo "order" coincide con la selección.
                const filtradas = todasLasAves.filter(x => x.info.order.value === ordenSeleccionado);

                // Insertamos el título y la lista vacía en el contenedor.
                resultado.innerHTML += `<h2>${ordenSeleccionado}</h2>`;
                resultado.innerHTML += `<ol id="lista-aves"></ol>`;

                // Recorremos el subarreglo filtrado y añadimos un <li> por cada ave.
                filtradas.forEach((x) => {
                    document.getElementById("lista-aves").innerHTML += `<li><img src="${x.image.url}" class="tiny"/>${x.names.spanish}</li>`;
                });
            }

            // Quedamos pendientes del "change" en el select. Si hay "change", le pasamos el valor elegido a renderizarAves().
            select.addEventListener("change", function () {
                renderizarAves(this.value);
            });
        </script>
    </body>
</html>
```

- - - - - - - 

#### ¿Qué cambió aquí?

1. **Limpieza del HTML:** Ya no tenemos contenedores vacíos u ocultos esperando ser llenados. El HTML está limpio.
2. **Uso de `filter()`:** En lugar de recorrer todos los datos y preguntar con un `if` dentro del bucle, creamos un nuevo arreglo que solo contiene lo que el usuario quiere ver.
3. **Generación de Opciones:** El menú `select` se adapta solo. Si la API agrega un nuevo orden de aves mañana, el código lo incluirá automáticamente sin que toques el HTML.

- - - - - - - 


### Práctica (para la clase)

**El desafío:** Modifiquemos el comportamiento del "select" actual. Intentemos que, en lugar de filtrar por "Orden", el filtro funcione por otra categoría de la data (por ejemplo, por familia o estado de conservación) con la menor cantidad de cambios posibles al código recién presentado.


###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-10) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-12)
