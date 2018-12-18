---
title: Nástroj příkazového řádku ve Vizualizéru souběžnosti (CVCollectionCmd) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee6ba9335cee43a36750dfcdf46faed16c56db4e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790982"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Nástroj příkazového řádku Vizualizéru souběžnosti (CVCollectionCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít nástroj příkazového řádku Vizualizéru souběžnosti (CVCollectionCmd.exe) ke shromažďování trasování z příkazového řádku, takže můžete je zobrazit v Concurrency Visualizer pro sadu Visual Studio. Ostupné fondy lze použít v počítačích, v nichž není nainstalována sada Visual Studio.  
  
> [!NOTE]
>  Spouští se v sadě Visual Studio 2013, Vizualizátor souběžnosti je volitelné rozšíření. (Dříve to bylo byl součástí sady Visual Studio.) Můžete stáhnout [Concurrency Visualizer kolekce nástrojů pro Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103) ze služby Stažení softwaru.  
  
## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Stáhněte si nástroj příkazového řádku Vizualizéru souběžnosti  
 Chcete-li stáhnout a nainstalovat nástroj příkazového řádku, přejděte na [Concurrency Visualizer kolekce nástrojů pro Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103) a postupujte podle pokynů. Ve výchozím nastavení, CVCollectionCmd.exe nachází v %ProgramFiles%\Microsoft Tools\ kolekce Vizualizéru souběžnosti (% ProgramFiles (x86) %\Microsoft Tools\ kolekce Vizualizátor souběžnosti na x64 počítače).  
  
## <a name="collect-a-trace-with-cvcollectioncmd"></a>Shromažďovat trasování pomocí CVCollectionCmd  
 Spuštěním aplikace s CVCollectionCmd nebo připojením k němu můžete shromažďovat trasování. Podívejte se přehled příkazů níže pro vaše možnosti. Příklad  
  
```  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  
  
## <a name="commands-and-parameters"></a>Příkazy a parametry  
 Chcete-li získat nápovědu pro příkazy a parametry v nástroji příkazového řádku, zadejte na příkazovém řádku to:  
  
 **CvCollectionCmd /?**  
  
|Možnost|Popis|Parametry|Vrácené hodnoty|  
|------------|-----------------|----------------|-------------------|  
|Dotazy|Vrátí, zda shromažďování lze spustit.|Žádné|0, pokud kolekce je připraven ke spuštění.<br /><br /> 1, pokud kolekce je již spuštěna.<br /><br /> 2, pokud kolekce není v průběhu, ale jeden nebo více požadovaných [trasování událostí pro Windows](http://msdn.microsoft.com/library/ac99a063-e2d2-40cc-b659-d23c2f783f92) relace je již povolen.|  
|Spuštění|Spustí zadaný procesu v rámci Vizualizátor souběžnosti.|Cesta ke spustitelnému souboru.|0, pokud spuštění úspěšné.<br /><br /> 1, pokud spuštění selhalo, protože nebylo možné spustit cílovou aplikaci.<br /><br /> 13, pokud spuštění selhalo, protože CVCollectionCmd nemá dostatečná oprávnění k zápisu do zadaného výstupního adresáře.|  
|Připojit|Začne sběr trasování celého systému; v opačném případě připojí k procesu, pokud je zadaná.|Žádné|0, pokud byla úspěšná přílohy.<br /><br /> 1 pro přílohy se nezdařilo, protože určený proces je neplatný nebo nejednoznačný.<br /><br /> 13 Pokud přílohy se nezdařilo, protože CVCollectionCmd nemá dostatečná oprávnění k zápisu do zadaného výstupního adresáře:.|  
|Odpojit|Zastaví shromažďování.|Žádné|0, pokud bylo úspěšné odpojení.<br /><br /> 1 pro odpojení se nezdařilo, protože kolekce není právě probíhá.<br /><br /> 2, pokud odpojení se nezdařilo, protože kolekce se nepovedlo zastavit.|  
|Analyzovat|Analyzuje zadanou trasování.|Úplná cesta soubor CVTrace.|0, pokud byla analýza úspěšná.<br /><br /> 1, pokud analýzy nelze spustit, protože zadaný trasování byl celý systém, ale není zadaný žádný cílový proces.<br /><br /> byl zadán 2, pokud analýzy nelze spustit, protože trasování nebylo celý systém a proces.<br /><br /> 3, pokud analýza se nezdařila, protože určený proces je neplatný.<br /><br /> 4, pokud analýza se nezdařila, protože zadaný soubor CVTrace není platný.|  
|LaunchArgs|Určuje cílový spustitelný argumenty. Tato možnost se vztahuje na příkaz spustit.|Argumenty příkazového řádku pro aplikaci.|Žádné|  
|OutDir|Určuje adresář, do kterého chcete uložit soubory trasování. Platí pro příkazy spuštění a připojení.|Cesta k adresáři nebo relativní cestu.|Žádné|  
|Proces|Určuje proces pro připojení při provádění příkazu připojit nebo procesu trasování analyzovat při spuštění příkazu Analyze. Platí pro příkazy připojit a analyzovat.|Název procesu nebo PID.|Žádné|  
|Konfigurace|Určuje cestu k souboru konfigurace, pokud chcete kolekci nastavení jiné než výchozí hodnoty.   Platí pro příkazy spuštění, připojit a analyzovat.|Cesta k adresáři nebo relativní cesta ke konfiguračnímu souboru XML.|Žádné|  
  
## <a name="customizing-configuration-settings"></a>Přizpůsobení nastavení konfigurace  
 Pokud chcete upravit nastavení kolekce shromažďovat trasování pomocí CVCollectionCmd, použijte konfigurační soubor se zadávají.  
  
> [!NOTE]
>  Když shromažďovat trasování pomocí sady Visual Studio, nemusíte upravovat přímo konfiguračního souboru.  Místo toho použijte [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno Upravit nastavení.  
  
 Pokud chcete upravit nastavení shromažďování, vytvořte soubor konfigurace na počítači, kde budete spouštět nástroj CVCollectionCmd. Konfigurační soubor můžete vytvořit úplně od začátku, nebo můžete zkopírovat konfigurační soubor na počítači, který má nainstalovanou sadu Visual Studio a upravit. Soubor `UserConfig.xml` a nachází se v **místní AppData** složky. Když spustíte nástroj, použijte možnost konfigurace ve spojení s příkazem spuštění, připojit a analyzovat.  V parametru, který je spojen s možností konfigurace zadejte cestu konfigurační soubor.  
  
### <a name="configuration-file-tags"></a>Konfigurační soubor značek  
 Konfigurační soubor je založený na formátu XML. Zde jsou platné značky a hodnoty:  
  
|Značka|Popis|Hodnoty|  
|---------|-----------------|------------|  
|Konfigurace|Vymezuje pásma celkové konfiguračního souboru.|Musí obsahovat tyto prvky:<br /><br /> -Podverze<br />-Hlavní verze|  
|Hlavní verze|Určuje hlavní verzi konfiguračního souboru.|Musí být 1 pro [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projekty. Pokud ne 1, nástroj nebude fungovat.|  
|Podverze|Určuje dílčí verze konfiguračního souboru.|Musí být 0 pro [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projekty. Pokud není 0, nástroj nebude fungovat.|  
|IncludeEnvSymbolPath|Nastaví hodnotu, která určuje, zda se používá cestu k symbolu prostředí (_NT_SYMBOL_PATH).|-True<br />-False|  
|DeleteEtlsAfterAnalysis|Nastaví hodnotu, která určuje, jestli se po dokončení analýzy odstranit soubory ETL.|-True<br />-False|  
|Symbolpath –|Určuje cestu k serveru symbolů. Další informace najdete v tématu [použijte Microsoft Symbol Server k získání souborů se symboly ladění](http://go.microsoft.com/fwlink/?LinkID=149389).|Název adresáře nebo adresu URL.|  
|Značky|Obsahuje seznam zprostředkovatelů značky.|Může obsahovat nula nebo více prvků MarkerProvider.|  
|MarkerProvider|Určuje zprostředkovatele jednu značku.|Musí obsahovat tyto prvky:<br /><br /> -Úroveň<br />-IDENTIFIKÁTOR GUID<br />– Název<br /><br /> Může obsahovat tyto prvky:<br /><br /> -Kategorie<br />-IsEnabled|  
|úroveň|Nastaví úroveň důležitosti MarkerProvider.|– Nízká<br />-Normální<br />– Vysoká<br />– Kritické<br />-Vše|  
|identifikátor GUID|Globálně jedinečný identifikátor poskytovatele trasování událostí pro Windows značek.|IDENTIFIKÁTOR GUID.|  
|Název|Určuje popis poskytovatele značek.|Řetězec.|  
|Kategorie|Určuje kategorie shromážděných pro poskytovatele značek.|Řetězec oddělených čárkou čísla nebo rozsahy čísel.|  
|hodnotu isEnabled|Nastaví hodnotu, která určuje, zda je povoleno poskytovatele značek pro kolekci.|-True<br />-False|  
|FilterConfig|Určuje seznam možností konfigurace událostí trasování událostí pro Windows, které jsou filtrovány z kolekce.|Může obsahovat tyto prvky:<br /><br /> -CollectClrEvents<br />-ClrCollectionOptions<br />-CollectSampleEvents<br />-CollectGpuEvents<br />-CollectFileIO|  
|CollectClrEvents|Nastavte hodnotu, která určuje, zda budou shromažďovány události CLR.|-True<br />-False|  
|ClrCollectionOptions|Určuje, jestli se má shromažďovat události CLR pro nativní aplikace a jestli se mají shromažďovat události rundown NGEN.|Může obsahovat jednu, oba nebo žádná z těchto hodnot:<br /><br /> -CollectForNative<br />-DisableNGenRundown|  
|CollectSampleEvents|Nastaví hodnotu, která určuje, zda budou shromažďovány události vzorku.|-True<br />-False|  
|CollectGpuEvents|Nastaví hodnotu, která určuje, zda budou shromažďovány události generované modulem DX.|-True<br />-False|  
|CollectFileIO|Nastaví hodnotu, která určuje, zda budou shromažďovány události vstupu a výstupu souborů.|-True<br />-False|  
|UserBufferSettings|Určuje seznam parametrů uživatelské nastavení vyrovnávací paměti.|Musí obsahovat tyto prvky:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|KernelBufferSettings|Určuje seznam parametrů nastavení vyrovnávací paměti jádra.|Musí obsahovat tyto prvky:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|BufferFlushTimer|Určuje zarovnávací časovače vyrovnávací paměti trasování událostí pro Windows.|Kladné celé číslo.|  
|BufferSize|Množství paměti přidělené pro každé vyrovnávací paměti trasování událostí relace, v kilobajtech.|Číslo od 0 do 1 024.|  
|MinimumBuffers|Minimální počet vyrovnávacích pamětí, které jsou přiděleny pro fond vyrovnávací paměti relace trasování událostí.|Kladné celé číslo větší než nebo rovna hodnotě dvojnásobný počet logických jader.|  
|MaximumBuffers|Maximální počet vyrovnávacích pamětí, které jsou přiděleny pro fond vyrovnávací paměti relace trasování událostí.|Číslo větší než nebo rovna hodnotě MinimumBuffers.|  
|JustMyCode|Určuje seznam adresářů pouze můj kód.|Seznam nula nebo více prvků MyCodeDirectory.|  
|MyCodeDirectory|Určuje adresář, který obsahuje váš kód.|Absolutní cesta.|  
  
### <a name="example"></a>Příklad  
 Místo vytváření konfiguračního souboru od začátku, můžete zkopírovat následující příklad a následně upravit tak, aby vyhovovala vašim požadavkům.  
  
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



