L’hardware dell’X400 è costituito da due CPU principali:
Iomote Core: tramite l’Iomote_framework si occupa di gestire la connessione verso l’IoT Hub, lo scaricamento degli aggiornamenti e di garantire la sicurezza e la riservatezza delle comunicazioni. Integra la comunicazione ethernet e 3G.
Application processor: è in grado di far girare codice Arduino-compatibile, quindi può essere programmato con facilità attraverso la IDE di Arduino. E’ il micro che si occupa di eseguire la user app, per interagire con il mondo fisico attraverso una serie di IO analogici e digitali e numerosi bus di campo (VD. PINOUT ARDUINO)
I due processori comunicano attraverso una connessione seriale, gestita dalla user app tramite un semplice set di comandi (API), che permettono di comunicare con il cloud in maniera estremamente semplice. 


Attraverso la Iomoteplatform è possibile monitorare lo stato dei device e gestire eventi particolarmente significativi come:
provisioning: sarà possibile accoppiare con facilità i device al proprio account utente.
Iomote core update: l’iomote core fa girare l’iomote_framework, che consente di comunicare in maniera sicura con il cloud. Per garantire che la piattaorma resti sempre aggiornata con gli ultimi protocolli di sicurezza, saranno necessari degli aggiornamenti del framework, che potranno essere avviati e monitorati direttamente dal cloud. 
Aggiornamento app utente: sul cloud viene costantemente indicato il nome e la versione della app che gira su ogni singolo device. Sarà possibile aggiornare tale applicazione selezionando il file eseguibile direttamente da una repository presente sulla piattaforma, su cui sarà possibile scegliere sia l’applicazione che la relativa versione.

<li class="collection-item avatar gdev gdev-58cd32ef-f9a7-4631-b572-a5b36bbf64ac device-status-Connected" id="X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d">
    <img class="template_img circle" src="/images/ic_developer_board_black_24dp_2x.png" alt="">
    <div class="row no-margin">
        <div class="col s12 m6">
            <div class="template_title title">Iomote office</div>
            <div class="template_type subtitle">X400</div>
        </div>
        <div class="col s12 m6 subtitle">
            <div class="template_firmware">FW: 0.3.4</div>
            <div class="template_app">am2305 alarms 0.1.8</div>
        </div>
    </div>
    <span class="template_signal secondary-content" style="margin-right:30px"><i class="material-icons">brightness_1</i></span>
    <a href="javascript:OnOpenDevice('X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d')" class="template_button secondary-content"><i class="material-icons">send</i></a>
</li>

<li class="collection-item avatar gdev gdev-58cd32ef-f9a7-4631-b572-a5b36bbf64ac device-status-Connected active" id="X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d">
    <img class="template_img circle" src="/images/ic_developer_board_black_24dp_2x.png" alt="">
    <div class="row no-margin">
        <div class="col s12 m6">
            <div class="template_title title">Test device #1</div>
            <div class="template_type subtitle">X400</div>
        </div>
        <div class="col s12 m6 subtitle">
            <div class="template_firmware">FW: 0.3.4</div>
            <div class="template_app">Temp sensors 0.1.8</div>
        </div>
    </div>
    <span class="template_signal secondary-content" style="margin-right:30px"><i class="material-icons">brightness_1</i></span>
    <a href="javascript:OnOpenDevice('X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d')" class="template_button secondary-content"><i class="material-icons">send</i></a>
</li>

<li class="collection-item avatar gdev gdev-58cd32ef-f9a7-4631-b572-a5b36bbf64ac device-status-Connected" id="X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d">
    <img class="template_img circle" src="/images/ic_developer_board_black_24dp_2x.png" alt="">
    <div class="row no-margin">
        <div class="col s12 m6">
            <div class="template_title title">CNC machine #1</div>
            <div class="template_type subtitle">X400</div>
        </div>
        <div class="col s12 m6 subtitle">
            <div class="template_firmware">FW: 0.3.4</div>
            <div class="template_app">CNC monitor 1.2.1</div>
        </div>
    </div>
    <span class="template_signal secondary-content" style="margin-right:30px"><i class="material-icons">brightness_1</i></span>
    <a href="javascript:OnOpenDevice('X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d')" class="template_button secondary-content"><i class="material-icons">send</i></a>
</li>

<li class="collection-item avatar gdev gdev-58cd32ef-f9a7-4631-b572-a5b36bbf64ac device-status-Connected" id="X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d">
    <img class="template_img circle" src="/images/ic_developer_board_black_24dp_2x.png" alt="">
    <div class="row no-margin">
        <div class="col s12 m6">
            <div class="template_title title">CNC machine #2</div>
            <div class="template_type subtitle">X400</div>
        </div>
        <div class="col s12 m6 subtitle">
            <div class="template_firmware">FW: 0.3.4</div>
            <div class="template_app">CNC monitor 1.2.1</div>
        </div>
    </div>
    <span class="template_signal secondary-content" style="margin-right:30px"><i class="material-icons">brightness_1</i></span>
    <a href="javascript:OnOpenDevice('X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d')" class="template_button secondary-content"><i class="material-icons">send</i></a>
</li>


<li class="collection-item avatar gdev gdev-58cd32ef-f9a7-4631-b572-a5b36bbf64ac device-status-Connected" id="X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d">
    <img class="template_img circle" src="/images/ic_developer_board_black_24dp_2x.png" alt="">
    <div class="row no-margin">
        <div class="col s12 m6">
            <div class="template_title title">Outdoor sensors</div>
            <div class="template_type subtitle">X400</div>
        </div>
        <div class="col s12 m6 subtitle">
            <div class="template_firmware">FW: 0.3.4</div>
            <div class="template_app">sensing 0.9.3</div>
        </div>
    </div>
    <span class="template_signal secondary-content" style="margin-right:30px"><i class="material-icons">brightness_1</i></span>
    <a href="javascript:OnOpenDevice('X400_9637eb6ea6c59ad7867cdba6e4c76dd5c8cd933d')" class="template_button secondary-content"><i class="material-icons">send</i></a>
</li>