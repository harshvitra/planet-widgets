<script>
    import { getFormattedNumber } from "./../../utils/formatNumber";
    export let data;
    let radius = 140;
    let size = 154;
    let circumference = 2 * Math.PI * radius;
    
</script>

<div class="treeCounterContainer">
        <div class="mainContainer">
            <div class="treeCounterComponent">
                <div class="treeCounter">
                    <div class="textContainer">
                        <p class="treecount">
                            {getFormattedNumber(
                                data.score.personal + data.score.received
                            )}
                        </p>
                        <p class="treecountLabel">Trees Planted</p>
                    </div>
                    {#if data.score.target !=0}
                    <div class="textContainer">
                        <p class="treecount">
                            {getFormattedNumber(data.score.target)}
                        </p>
                        <p class="treecountLabel">Target</p>
                    </div>
                    {/if}   
                </div>

            <svg style={`width:${size*2}px; height:${size*2}px;position:absolute;`}>
                <circle
                cx={size}
                cy={size}
                r={radius}
                stroke="#68b030"
                stroke-linecap="round"
                stroke-width="24"
                transform={`rotate(-90,${size},${size})`}
                stroke-dasharray={circumference}
                stroke-dashoffset={circumference * (1- (data.score.personal + data.score.received)/data.score.target)}
                fill="transparent"
                />
            </svg>
            </div>
            <a href={`${__myapp.env.APP_URL}/s/${data.slug}`} class="primaryButton" on:click target="_blank">
               Plant Trees
            </a>
        </div>
</div>

<style>
    .mainContainer {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: fixed;
        top:24px;
        left: 60px;
    }
    .treeCounterContainer {
        height: 420px;
        width: 420px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    .treeCounterComponent {
        height: 300px;
        width: 300px;
        background-image: radial-gradient(white 0%, white 60%, #47a8dc 100%);
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
    }
    .treeCounter {
        height: 266px;
        width: 266px;
        border-radius: 50%;
        background-color: #23519b;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
    }
    .treecount {
        font-size: 48px;
        font-weight: bold;
        text-align: center;
        color: white;
    }
    .treecountLabel {
        font-size: 13px;
        font-weight: bold;
        text-align: center;
        color: white;
        margin-top: 6px;
    }
    .primaryButton {
        color: white;
        font-weight: bold;
        background-color: #68b030;
        height: 52px;
        padding: 0px;
        text-align: center;
        border: 0px;
        border-radius: 52px;
        min-width: 280px;
        margin-top: 24px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .primaryButton:hover{
        text-decoration: none;
        cursor: pointer;
        position: relative;
        color: white;
        font-weight: bold;
        background-color: #68b030;
        height: 55px;
        padding: 0px;
        text-align: center;
        border: 0px;
        border-radius: 52px;
        min-width: 290px;
        margin-top: 24px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 17px;
    }
</style>
