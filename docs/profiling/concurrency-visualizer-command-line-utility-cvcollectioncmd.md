---
title: Nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911209"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd)
Nástroj příkazového řádku Vizualizátor souběžnosti (*CVCollectionCmd.exe*) můžete použít ke shromáždění trasování z příkazového řádku, abyste je mohli zobrazit v Vizualizátor souběžnosti pro Visual Studio. Nástroje lze použít na počítačích, ve kterých není nainstalována aplikace Visual Studio.

> [!NOTE]
> Počínaje Visual Studio 2013 je Vizualizátor souběžnosti volitelné rozšíření. (Dřív byl součástí sady Visual Studio.) [Nástroje kolekce Vizualizátor souběžnosti pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) si můžete stáhnout z webu Stažení softwaru.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Stáhnout nástroj příkazového řádku Vizualizátor souběžnosti
 Pokud chcete stáhnout a nainstalovat nástroj příkazového řádku, přejděte na [nástroje kolekce Vizualizátor souběžnosti pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) a postupujte podle pokynů. Ve výchozím nastavení se *CVCollectionCmd.exe* nainstaluje v nástroji kolekce Vizualizátor souběžnosti%ProgramFiles%\Microsoft \ (% ProgramFiles (x86)% \ nástroje kolekce Vizualizátor souběžnosti Microsoft Concurrency \ na počítačích x64).

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Shromažďování trasování pomocí CVCollectionCmd
 Trasování můžete shromáždit spuštěním aplikace pomocí CVCollectionCmd nebo jejich připojením. Možnosti najdete níže v referenčních informacích k příkazu. Například

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Příkazy a parametry
 Nápovědu k příkazům a parametrům v nástroji příkazového řádku získáte zadáním tohoto příkazu do příkazového řádku:

 **CvCollectionCmd/?**

|Možnost|Popis|Parametry|Vrácené hodnoty|
|------------|-----------------|----------------|-------------------|
|Dotaz|Vrátí, zda lze kolekci spustit.|Žádné|0, pokud je kolekce připravena k zahájení.<br /><br /> 1, pokud kolekce již probíhá.<br /><br /> 2 Pokud shromažďování neprobíhá, ale jedna nebo více požadovaných relací [ETW](/dotnet/framework/wcf/samples/etw-tracing) je již povoleno.|
|Spuštění|Spustí zadaný proces v rámci Vizualizátor souběžnosti.|Cesta ke spustitelnému souboru.|0, pokud se spuštění zdařilo.<br /><br /> 1, pokud se spuštění nepovedlo, protože cílovou aplikaci se nepovedlo spustit.<br /><br /> 13 Pokud se spuštění nepovedlo, protože CVCollectionCmd nemá dostatečná oprávnění k zápisu do zadaného výstupního adresáře.|
|Připojit|Začíná shromažďovat trasování v rámci systému. v opačném případě připojí k procesu, je-li zadán.|Žádné|0, pokud byla příloha úspěšná<br /><br /> 1 pokud příloha se nezdařila, protože zadaný proces je neplatný nebo nejednoznačný.<br /><br /> 13 Pokud se příloha nezdařila, protože CVCollectionCmd nemá dostatečná oprávnění k zápisu do zadaného výstupního adresáře.|
|Odpojit|Zastaví shromažďování.|Žádné|0, pokud bylo odpojení úspěšné.<br /><br /> 1, pokud se odpojení nepovedlo, protože kolekce momentálně neprobíhá.<br /><br /> 2, pokud se odpojení nepovedlo, protože se nepovedlo zastavit shromažďování.|
|Analýza|Analyzuje zadané trasování.|Úplná cesta k souboru CVTrace.|0, pokud se analýza zdařila.<br /><br /> 1, pokud se analýza nemůže spustit, protože zadané trasování bylo na úrovni systému, ale nezadal se žádný cílový proces.<br /><br /> 2 Pokud analýza nemůže začít, protože trasování nebylo pro systém a byl zadán proces.<br /><br /> 3 Pokud se analýza nezdařila, protože zadaný proces je neplatný.<br /><br /> 4 Pokud se analýza nezdařila, protože zadaný soubor CVTrace není platný.|
|Argumenty spuštění|Určuje argumenty cílového spustitelného souboru. Tato možnost se vztahuje pouze na příkaz pro spuštění.|Argumenty příkazového řádku pro aplikaci.|Žádné|
|OutDir|Určuje adresář, do kterého se mají ukládat trasovací soubory. Platí pro příkazy spustit a připojit.|Cesta k adresáři nebo relativní cesta.|Žádné|
|Proces|Určuje proces, který se má připojit ke spuštění příkazu připojit, nebo proces v trasování, který se má analyzovat při spuštění příkazu analyzovat. Platí pro příkazy připojit a analyzovat.|PID nebo název procesu.|Žádné|
|Config|Určuje cestu ke konfiguračnímu souboru, pokud chcete, aby nastavení kolekce byla jiné než výchozí.   Platí pro příkazy spustit, připojit a analyzovat.|Cesta k adresáři nebo relativní cesta ke konfiguračnímu souboru XML.|Žádné|

## <a name="customize-configuration-settings"></a>Přizpůsobení nastavení konfigurace
 Použijete-li CVCollectionCmd ke shromáždění trasování a chcete upravit nastavení kolekce, pak použijte konfigurační soubor a určete je.

> [!NOTE]
> Když použijete Visual Studio ke shromáždění trasování, neupravujte přímo konfigurační soubor.  Místo toho upravte nastavení pomocí dialogového okna [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) .

 Chcete-li upravit nastavení kolekce, vytvořte na počítači, kde budete spouštět nástroj CVCollectionCmd, konfigurační soubor. Můžete vytvořit konfigurační soubor od začátku nebo můžete zkopírovat konfigurační soubor na počítači, kde je nainstalována aplikace Visual Studio, a upravit. Soubor je pojmenován *UserConfig.xml* a je umístěn v místní složce pro *data aplikací* . Když nástroj spustíte, použijte možnost konfigurace ve spojení s příkazem spustit, připojit nebo analyzovat.  V parametru, který je přidružený k možnosti konfigurace, zadejte cestu ke konfiguračnímu souboru.

### <a name="configuration-file-tags"></a>Značky konfiguračního souboru
 Konfigurační soubor je založen na formátu XML. Tady jsou platné značky a hodnoty:

| Značka | Popis | Hodnoty |
|-------------------------| - | - |
| Config | Vymezí celkový konfigurační soubor. | Musí obsahovat tyto prvky:<br /><br /> – Podverze<br />– MajorVersion |
| MajorVersion | Určuje hlavní verzi konfiguračního souboru. | Pro projekty musí být 1 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Pokud ne, nástroj nebude fungovat. |
| Podverze | Určuje dílčí verzi konfiguračního souboru. | Pro projekty musí být 0 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Pokud není 0, nástroj nebude fungovat. |
| IncludeEnvSymbolPath | Nastaví hodnotu, která určuje, zda je použita cesta k symbolu prostředí (_NT_SYMBOL_PATH). | – True<br />– False |
| DeleteEtlsAfterAnalysis | Nastaví hodnotu, která určuje, zda jsou po dokončení analýzy odstraněny soubory ETL. | – True<br />– False |
| SymbolPath | Určuje cestu k serveru symbolů. Další informace najdete v tématu [použití symbolového serveru Microsoftu k získání souborů se symboly ladění](/windows/win32/dxtecharts/debugging-with-symbols). | Název nebo adresa URL adresáře. |
| Značky | Obsahuje seznam poskytovatelů značek. | Může obsahovat nula nebo více elementů MarkerProvider. |
| MarkerProvider | Určuje jednoho zprostředkovatele značek. | Musí obsahovat tyto prvky:<br /><br /> -Úroveň<br />– GUID<br />– Název<br /><br /> Může obsahovat tyto prvky:<br /><br /> – Kategorie<br />-Povoleno |
| Úroveň | Nastaví úroveň důležitosti MarkerProvider. | – Nízká<br />– Normální<br />-Vysoká<br />– Kritické<br />– Vše |
| Identifikátor GUID | Globálně jedinečný identifikátor zprostředkovatele značek ETW. | IDENTIFIKÁTOR GUID. |
| Název | Určuje popis poskytovatele značek. | Řetězec. |
| Kategorie | Určuje kategorie shromážděné pro poskytovatele značek. | Řetězec čísel nebo rozsahů čísel oddělených čárkami. |
| IsEnabled | Nastaví hodnotu, která určuje, zda je zprostředkovatel značek povolen pro kolekci. | – True<br />– False |
| FilterConfig | Určuje seznam možností konfigurace událostí ETW, které jsou filtrovány z kolekce. | Může obsahovat tyto prvky:<br /><br /> - CollectClrEvents<br />- ClrCollectionOptions<br />- CollectSampleEvents<br />- CollectGpuEvents<br />- CollectFileIO |
| CollectClrEvents | Nastavte hodnotu, která určuje, zda jsou shromažďovány události CLR. | – True<br />– False |
| ClrCollectionOptions | Určuje, jestli se mají shromažďovat události CLR pro nativní aplikace a jestli se mají shromažďovat události doběhu NGEN. | Může obsahovat jednu, nebo žádnou z těchto hodnot:<br /><br /> - CollectForNative<br />- DisableNGenRundown |
| CollectSampleEvents | Nastaví hodnotu, která určuje, zda jsou shromažďovány ukázkové události. | – True<br />– False |
| CollectGpuEvents | Nastaví hodnotu, která určuje, zda jsou shromažďovány události generované rozhraním DX. | – True<br />– False |
| CollectFileIO | Nastaví hodnotu, která určuje, zda jsou shromažďovány vstupně-výstupní události souboru. | – True<br />– False |
| UserBufferSettings | Určuje seznam parametrů nastavení vyrovnávací paměti uživatele. | Musí obsahovat tyto prvky:<br /><br /> - BufferFlushTimer<br />– BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| KernelBufferSettings | Určuje seznam parametrů nastavení vyrovnávací paměti jádra. | Musí obsahovat tyto prvky:<br /><br /> - BufferFlushTimer<br />– BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| BufferFlushTimer | Určuje časovač vyprázdnění vyrovnávací paměti trasování událostí pro Windows. | Kladné celé číslo. |
| BufferSize | Velikost paměti, která je přidělena pro každou vyrovnávací paměť relace trasování událostí v kilobajtech. | Číslo od 0 do 1024. |
| MinimumBuffers | Minimální počet vyrovnávacích pamětí, které jsou přiděleny fondu vyrovnávacích pamětí relace trasování událostí. | Kladné celé číslo větší než nebo rovno dvojnásobku počtu logických jader. |
| MaximumBuffers | Maximální počet vyrovnávacích pamětí, které jsou přiděleny fondu vyrovnávacích pamětí relace trasování událostí. | Číslo větší nebo rovno MinimumBuffers. |
| JustMyCode | Určuje seznam adresářů Pouze můj kód. | Seznam nula nebo více elementů MyCodeDirectory. |
| MyCodeDirectory | Určuje adresář, který obsahuje váš kód. | Absolutní cesta. |

### <a name="example"></a>Příklad
 Místo vytvoření konfiguračního souboru od začátku můžete zkopírovat následující příklad a pak ho upravit tak, aby splňoval vaše požadavky.

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
