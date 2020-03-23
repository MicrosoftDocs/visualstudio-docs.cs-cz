---
title: Nástroj příkazového řádku vizualizéru souběžnosti (CVCollectionCmd) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2721798ee9f0c7e006acdedbecaecbd56068be3f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911209"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Nástroj příkazového řádku vizualizéru souběžnosti (CVCollectionCmd)
Nástroj příkazového řádku souběžnosti Visualizer (*CVCollectionCmd.exe*) můžete použít ke shromažďování trasování z příkazového řádku, abyste je mohli zobrazit v vizualizéru souběžnosti pro visual studio. Nástroje lze použít v počítačích, ve kterých není nainstalována sada Visual Studio.

> [!NOTE]
> Počínaje Visual Studio 2013, Vizualizér souběžnosti je volitelné rozšíření. (Dříve byla zahrnuta do sady Visual Studio.) Nástroje kolekce [Vizualizérů souběžnosti pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) si můžete stáhnout ze služby Stažení softwaru.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Stažení nástroje příkazového řádku Vizualizéru souběžnosti
 Chcete-li stáhnout a nainstalovat nástroj příkazového řádku, přejděte na [nástroje kolekce vizuálů souběžnosti pro visual studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) a postupujte podle pokynů. Ve výchozím nastavení je *program CVCollectionCmd.exe* nainstalován v %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ v počítačích x64).

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Sbírat trasování s CVCollectionCmd
 Můžete shromažďovat trasování spuštěním aplikace s CVCollectionCmd, nebo připojením k němu. Podívejte se na odkaz na příkaz níže pro vaše možnosti. Například

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Příkazy a parametry
 Chcete-li získat nápovědu k příkazům a parametrům v nástroji příkazového řádku, zadejte tuto možnost na příkazovém řádku:

 **CvCollectionCmd /?**

|Možnost|Popis|Parametry|Vrácené hodnoty|
|------------|-----------------|----------------|-------------------|
|Dotaz|Vrátí, zda lze spustit kolekci.|Žádný|0, pokud je kolekce připravena ke spuštění.<br /><br /> 1, pokud kolekce již probíhá.<br /><br /> 2 Pokud kolekce neprobíhá, ale jedna nebo více požadovaných relací [ETW](/dotnet/framework/wcf/samples/etw-tracing) je již povolena.|
|Spuštění|Spustí zadaný proces v rámci vizualizéru souběžnosti.|Cesta spustitelného souboru.|0, pokud bylo spuštění úspěšné.<br /><br /> 1, pokud se spuštění nezdařilo, protože cílovou aplikaci nelze spustit.<br /><br /> 13 Pokud se spuštění nezdařilo, protože CVCollectionCmd nemá dostatečná oprávnění k zápisu do zadaného výstupního adresáře.|
|Připojit|Začíná shromažďovat trasování celého systému; v opačném případě se připojí k procesu, pokud je zadán.|Žádné.|0, pokud byla příloha úspěšná.<br /><br /> 1 Pokud se příloha nezdařila, protože zadaný proces je neplatný nebo nejednoznačný.<br /><br /> 13 Pokud se příloha nezdařila, protože CVCollectionCmd nemá dostatečná oprávnění k zápisu do zadaného výstupního adresáře.|
|Odpojit|Zastaví shromažďování.|Žádné.|0, pokud oddělení proběhlo úspěšně.<br /><br /> 1 Pokud oddělení se nezdařilo, protože kolekce není aktuálně probíhá.<br /><br /> 2 Pokud oddělení se nezdařilo, protože kolekce nemohla být zastavena.|
|Analýza|Analyzuje zadané trasování.|Úplná cesta k souboru CVTrace.|0, pokud byla analýza úspěšná.<br /><br /> 1 Pokud analýzu nelze spustit, protože zadané trasování bylo celé ho systému, ale nebyl zadán žádný cílový proces.<br /><br /> 2 Pokud analýzu nelze spustit, protože trasování nebylo v celém systému a byl zadán proces.<br /><br /> 3, pokud se analýza nezdařila, protože zadaný proces je neplatný.<br /><br /> 4, pokud se analýza nezdařila, protože zadaný soubor CVTrace je neplatný.|
|LaunchArgs|Určuje cílové spustitelné argumenty. Tato možnost platí pouze pro příkaz Spustit.|Argumenty příkazového řádku k aplikaci.|Žádné.|
|Outdir|Určuje adresář, do kterého mají být uloženy trasovací soubory. Platí pro příkazy Spustit a připojit.|Cesta k adresáři nebo relativní cesta.|Žádné.|
|Proces|Určuje proces, ke kterému se má připojit při spuštění příkazu Připojit, nebo proces ve stopování za účelem analýzy při spuštění příkazu Analyzovat. Platí pro příkazy Připojit a Analyzovat.|PID nebo název procesu.|Žádné.|
|Config|Určuje cestu konfiguračního souboru, pokud chcete, aby nastavení kolekce jiné než výchozí.   Platí pro příkazy Spustit, Připojit a Analyzovat.|Cesta k adresáři nebo relativní cesta konfiguračního souboru XML.|Žádné.|

## <a name="customize-configuration-settings"></a>Přizpůsobení nastavení konfigurace
 Pokud používáte CVCollectionCmd ke shromažďování trasování a chcete přizpůsobit nastavení kolekce, pak použijte konfigurační soubor k jejich určení.

> [!NOTE]
> Při použití sady Visual Studio ke shromažďování trasování, není přímo upravit konfigurační soubor.  Místo toho použijte dialogové okno [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) k úpravě nastavení.

 Chcete-li změnit nastavení kolekce, vytvořte konfigurační soubor v počítači, ve kterém spustíte nástroj CVCollectionCmd. Konfigurační soubor můžete vytvořit od začátku nebo můžete zkopírovat konfigurační soubor v počítači, ve který je nainstalována sada Visual Studio, a upravit jej. Soubor má název *UserConfig.xml* a je umístěn ve složce *Local AppData.* Při spuštění nástroje použijte možnost Konfigurace ve spojení s příkazem Spustit, Připojit nebo Analyzovat.  V parametru, který je přidružen k volbě Konfigurace, zadejte cestu konfiguračního souboru.

### <a name="configuration-file-tags"></a>Značky konfiguračních souborů
 Konfigurační soubor je založen na xml. Zde jsou platné značky a hodnoty:

| Značka | Popis | Hodnoty |
|-------------------------| - | - |
| Config | Vymezuje celkový konfigurační soubor. | Musí obsahovat tyto prvky:<br /><br /> - Menší verze<br />- Hlavní verze |
| Hlavní verze | Určuje hlavní verzi konfiguračního souboru. | Musí být [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 1 pro projekty. Pokud tomu tak není 1, nástroj nebude fungovat. |
| Minorversion | Určuje dílčí verzi konfiguračního souboru. | Musí být [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 0 pro projekty. Pokud ne 0, nástroj nebude fungovat. |
| Cesta symbolů IncludeEnv | Nastaví hodnotu, která určuje, zda je použita cesta symbolu prostředí (_NT_SYMBOL_PATH). | - Pravda<br />- Nepravdivé |
| OdstranitAnalýzu po odstranění | Nastaví hodnotu, která určuje, zda jsou soubory ETL odstraněny po dokončení analýzy. | - Pravda<br />- Nepravdivé |
| Cesta symbolu | Určuje cestu k serveru symbolů. Další informace naleznete [v tématu Získání souborů ladicích symbolů pomocí serveru Microsoft Symbol Server](/windows/win32/dxtecharts/debugging-with-symbols). | Název adresáře nebo adresa URL. |
| Značky | Obsahuje seznam zprostředkovatelů značek. | Může obsahovat nula nebo více MarkerProvider prvky. |
| MarkerProvider | Určuje jednoho zprostředkovatele značky. | Musí obsahovat tyto prvky:<br /><br /> - Úroveň<br />- IDENTIFIKÁTOR GUID<br />- Jméno<br /><br /> Může obsahovat tyto prvky:<br /><br /> - Kategorie<br />- Je povoleno |
| Úroveň | Nastaví úroveň důležitosti MarkerProvider. | - Nízká<br />- Normální<br />- Vysoká<br />- Kritické<br />- Všechno |
| Identifikátor GUID | Globálně jedinečný identifikátor poskytovatele značky ETW. | Identifikátor GUID. |
| Name (Název) | Určuje popis zprostředkovatele značky. | Řetězec. |
| Kategorie | Určuje kategorie shromážděné pro zprostředkovatele značek. | Řetězec čísel nebo rozsahů čísel oddělený chod čárky. |
| IsEnabled | Nastaví hodnotu, která určuje, zda je povoleno zprostředkovatele značky pro shromažďování. | - Pravda<br />- Nepravdivé |
| Funkce FilterConfig | Určuje seznam možností konfigurace událostí ETW, které jsou filtrovány z kolekce. | Může obsahovat tyto prvky:<br /><br /> - CollectClrEvents<br />- Možnosti shromažďování informací<br />- CollectSampleEvents<br />- Akce CollectGpu<br />- Collectfileio |
| CollectClrEvents | Nastavte hodnotu, která určuje, zda jsou shromažďovány události CLR. | - Pravda<br />- Nepravdivé |
| Možnosti shromažďování informací | Určuje, zda se mají shromažďovat události CLR pro nativní aplikace a zda má být shromažďování událostí rundown NGEN. | Může obsahovat jednu, obě nebo žádnou z těchto hodnot:<br /><br /> - CollectForNative<br />- ZakázatNGenRundown |
| CollectSampleEvents | Nastaví hodnotu, která určuje, zda jsou shromažďovány ukázkové události. | - Pravda<br />- Nepravdivé |
| Akce CollectGpu | Nastaví hodnotu, která určuje, zda jsou shromažďovány události generované DX. | - Pravda<br />- Nepravdivé |
| CollectfileIO | Nastaví hodnotu, která určuje, zda jsou shromažďovány události vstupně-no souboru. | - Pravda<br />- Nepravdivé |
| Nastavení uživatelského bufferu | Určuje seznam parametrů nastavení vyrovnávací paměti uživatele. | Musí obsahovat tyto prvky:<br /><br /> - BufferFlushTimer<br />- Velikost vyrovnávací paměti<br />- Minimální nárazníky<br />- Maximální vyrovnávací paměti |
| Nastavení vyrovnávací paměti jádra | Určuje seznam parametrů nastavení vyrovnávací paměti jádra. | Musí obsahovat tyto prvky:<br /><br /> - BufferFlushTimer<br />- Velikost vyrovnávací paměti<br />- Minimální nárazníky<br />- Maximální vyrovnávací paměti |
| BufferFlushTimer | Určuje časovač splachování vyrovnávacích pamětí ETW. | Kladné celé číslo. |
| Buffersize | Velikost paměti, která je přidělena pro každou vyrovnávací paměť relace trasování událostí v kilobajtech. | Číslo od 0 do 1024. |
| Minimální vyrovnávací paměti | Minimální počet vyrovnávacích pamětí, které jsou přiděleny pro fond vyrovnávací ch fondu relace trasování událostí. | Kladné celé číslo větší nebo rovno dvojnásobku počtu logických jader. |
| Maximální vyrovnávací paměti | Maximální počet vyrovnávacích pamětí, které jsou přiděleny pro fond vyrovnávacích pamětí relace trasování událostí. | Číslo větší nebo rovno MinimumBuffers. |
| JustMyCode | Určuje seznam adresářů Jen můj kód. | Seznam nula nebo více MyCodeDirectory prvky. |
| Adresář MyCodeDirectory | Určuje adresář, který obsahuje váš kód. | Absolutní cesta. |

### <a name="example"></a>Příklad
 Namísto vytváření konfiguračního souboru od začátku můžete zkopírovat následující příklad a potom jej upravit tak, aby vyhovoval vašim požadavkům.

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```
