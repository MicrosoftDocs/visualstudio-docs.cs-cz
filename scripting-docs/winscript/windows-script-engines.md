---
title: Skriptovací stroje Windows | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27a500f9df91738e2db563f7e37ee646925b674e
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835690"
---
# <a name="windows-script-engines"></a>Skriptovací stroje systému Windows
Chcete-li implementovat skriptovací stroj Microsoft Windows, vytvořte objekt OLE COM, který podporuje následující rozhraní.  
  
|||  
|-|-|  
|Rozhraní|Popis|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Poskytuje základní schopnost skriptování. Vyžaduje se implementace tohoto rozhraní.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Poskytuje možnost přidat text skriptu, vyhodnotit výrazy a tak dále. Implementace tohoto rozhraní je volitelná; Pokud však není implementován, skriptovací stroj musí implementovat jedno z rozhraní IPersist *, aby mohl načíst skript.|  
|IPersist*|Poskytuje podporu trvalosti. Pokud není implementována [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) , je vyžadována implementace alespoň jednoho z následujících rozhraní.<br /><br /> IPersistStorage: poskytuje podporu pro atribut DATA = {URL} ve značce OBJECT.<br /><br /> IPersistStreamInit: poskytuje podporu pro stejnou hodnotu stejně jako `IPersistStorage` atribut data = "datový proud bajtů kódovaný v řetězci" ve značce objektu.<br /><br /> IPersistPropertyBag: poskytuje podporu pro atribut PARAm = ve značce OBJECT.|  
  
> [!NOTE]
> Je možné, že skriptovací modul nebude nikdy volán k uložení nebo obnovení stavu skriptu pomocí `IPersist*` . Místo toho je [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) používán voláním [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) pro vytvoření prázdného skriptu, pak skriptlety jsou přidány a připojeny k událostem pomocí [IActiveScriptParse:: AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) a obecný kód je přidán pomocí [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md). Nicméně skriptovací stroj by měl plně implementovat aspoň jedno `IPersist*` rozhraní (nejlépe `IPersistStreamInit` ), protože se jiné hostitelské aplikace mohou pokusit o jejich použití.  
  
 Následující části popisují implementaci skriptovacího modulu Windows podrobněji.  
  
 Další informace najdete v referenčních informacích o [rozhraních skriptů Windows](../winscript/reference/windows-script-interfaces-reference.md) .  
  
## <a name="registry-standard"></a>Standardní registr  
 Skriptovací stroj Windows se může identifikovat pomocí identifikátorů kategorií. Skript systému Windows aktuálně definuje dva identifikátory kategorií.  
  
|||  
|-|-|  
|Kategorie|Popis|  
|CATID_ActiveScript|Označuje, že identifikátory tříd (CLSID) jsou skriptovací stroje Windows, které podporují, přinejmenším rozhraní [IActiveScript](../winscript/reference/iactivescript.md) a mechanizmus trvalosti ( `IPersistStorage` `IPersistStreamInit` rozhraní, nebo IPersistPropertyBag).|  
|CATID_ActiveScriptParse|Označuje, že identifikátory CLSID jsou skriptovací stroje Windows, které podporují, přinejmenším rozhraní [IActiveScript](../winscript/reference/iactivescript.md) a [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|  
  
 I když [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) není skutečným mechanismem trvalosti, podporuje metodu [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) , která je funkčně ekvivalentní `IPersist*::InitNew` .  
  
## <a name="script-engine-states"></a>Stavy skriptovacího stroje  
 Skriptovací stroj Windows může být v jakémkoli okamžiku v jednom z několika stavů.  
  
|||  
|-|-|  
|State|Popis|  
|neinicializované|Skript nebyl inicializován nebo načten pomocí rozhraní IPersist * nebo nemá sadu rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) . Skriptovací modul se většinou nedá použít v tomto stavu, dokud se skript nenačte.|  
|inicializované|Skript byl inicializován s `IPersist*` rozhraním a má nastavené rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) , ale není připojen k objektům hostitele a událostem jímky. Všimněte si, že tento stav jednoduše znamená, že `IPersist*::Load` `IPersist*::InitNew` metoda,, nebo [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) byla dokončena a byla volána metoda [IActiveScript:: SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) . Modul nemůže v tomto režimu spustit kód. Modul zařadí do fronty kód, který mu pošle prostřednictvím metody [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md) , a po přechodu na počáteční stav spustí kód.<br /><br /> Vzhledem k tomu, že jazyky se můžou výrazně lišit v sémantikě, skriptovací stroje nejsou pro podporu tohoto přechodu stavu nutné. Moduly, které podporují metodu [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md) , však musí podporovat tento přechod stavu. Hostitelé musí pro tento přechod připravit a provést příslušné akce: vydání aktuálního skriptovacího modulu, vytvoření nového skriptovacího stroje a volání `IPersist*::Load` , `IPersist*::InitNew` nebo [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) (a případně také volání [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md)). Použití tohoto přechodu by mělo být považováno za optimalizaci výše uvedeného postupu. Všimněte si, že všechny informace, které skriptovací stroj získal o názvech pojmenovaných položek, a informace o typu, které popisují pojmenované položky, zůstávají platné.<br /><br /> Vzhledem k tomu, že se jazyky značně liší, je obtížné definovat přesnou sémantiku tohoto přechodu. Skriptovací stroj se musí minimálně odpojit od všech událostí a uvolnit všechny SCRIPTINFO_IUNKNOWN ukazatele získané voláním metody [IActiveScriptSite:: GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) . Po opětovném spuštění skriptu musí modul znovu získat tyto ukazatele. Skriptovací modul by měl také resetovat skript zpátky do počátečního stavu, který je vhodný pro daný jazyk. VBScript například resetuje všechny proměnné a uchová veškerý kód přidaný dynamicky voláním [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md) s nastaveným příznakem SCRIPTTEXT_ISPERSISTENT. Jiné jazyky mohou potřebovat zachovat aktuální hodnoty (například Lispu, protože není k dispozici žádné oddělení kódu nebo dat) nebo by se obnovily do známého stavu (to zahrnuje i jazyky se staticky inicializovanými proměnnými).<br /><br /> Všimněte si, že přechod do stavu spuštění by měl mít stejnou sémantiku (to znamená, že by měl opustit skriptovací stroj ve stejném stavu) jako volání `IPersist*::Save` za účelem uložení skriptovacího modulu a následným voláním `IPersist*::Load` načtení nového skriptovacího stroje; tyto akce by měly mít stejnou sémantiku jako [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md). Skriptovací moduly, které ještě nejsou podporované `IActiveScript::Clone` `IPersist*` , nebo by se měly pečlivě zvážit, jak by se měl stejný přechod do stavu spuštění chovat, aby takový přechod nenarušil výše uvedené podmínky, `IActiveScript::Clone` Pokud `IPersist*` je nebo později přidaná podpora.<br /><br /> Během tohoto přechodu do počátečního stavu se skriptovací stroj po příslušných destruktorech odpojí od jímky událostí, a tak dále, spustí se ve skriptu. Aby se zabránilo tomu, že se tyto destruktory spustí, může hostitel nejprve přesunout skript do odpojeného stavu před přechodem do stavu spuštění.<br /><br /> Pomocí [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) můžete zrušit spuštěné vlákno skriptu bez čekání na aktuální události a tak dále, aby se dokončilo spouštění.|  
|Začínáme|Přechod z inicializovaného stavu do stavu zahájeno způsobí, že modul spustí jakýkoli kód, který byl zařazen do fronty v inicializovaném stavu. Modul může spustit kód ve stavu spuštěno, ale není připojen k žádné události přidané prostřednictvím metody [IActiveScript:: AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) . Modul může spustit kód voláním rozhraní IDispatch získaného z metody [IActiveScript:: GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) nebo voláním [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md). Je možné, že další inicializace na pozadí (progresivní načítání) stále probíhá a že volání metody [IActiveScript:: SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) se sadou příznaku SCRIPTSTATE_CONNECTED může způsobit, že se skript zablokuje, dokud se nedokončí inicializace.|  
|připojeno|Skript je načten a připojen pro události jímky z objektů hostitele. Pokud se jedná o přechod z inicializovaného stavu, skriptovací modul by měl přecházet ve stavu spuštěno, aby se prováděly nezbytné akce před vstupem do stavu připojení a připojením k událostem.|  
|propojení|Skript je načten a má běhový stav, ale je dočasně odpojen od událostí jímky od objektů hostitele. To se dá provést logicky (ignorující přijaté události) nebo fyzicky (volání IConnectionPoint:: informujte na příslušných přípojných bodech). Pokud se jedná o přechod z inicializovaného stavu, skriptovací modul by měl projít stavem začátek a provést potřebné akce před přechodem do odpojeného stavu. Jímky událostí, které jsou zpracovávány, jsou dokončeny před změnou stavu (pomocí [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) zrušení spuštěného vlákna skriptu). Tento stav je odlišen od inicializovaného stavu v tom, že přechod do tohoto stavu nezpůsobí, že se skript resetuje, běhový stav skriptu není resetován a procedura inicializace skriptu není provedena.|  
|closed|Skript byl zavřen. Skriptovací stroj už nefunguje a vrací chyby pro většinu metod.|  
  
 Následující obrázek znázorňuje vztahy mezi různými stavy skriptovacího stroje a zobrazuje metody, které způsobují přechody z jednoho stavu do druhého.  
  
 Následující ilustrace znázorňuje akce, které skriptovací modul provádí během různých přechodů mezi stavy.  
  
## <a name="scripting-engine-threading"></a>Vlákna skriptovacího stroje  
 Vzhledem k tomu, že je možné použít skriptovací stroj Windows v mnoha prostředích, je důležité udržovat jeho model spuštění co nejpružnější. Například hostitel na bázi serveru může potřebovat zachovat vícevláknový návrh při použití skriptu Windows v rámci efektivního způsobu. Zároveň hostitel, který nepoužívá zřetězení, jako je například Typická aplikace, by neměl být zatížen správou vláken. Skript Windows dosahuje tohoto zůstatku tím, že omezuje možnosti zpětného volání skriptovacího stroje s volnými vlákny, které se můžou volat zpátky na hostitele, a uvolňuje tak hostitele z tohoto režie.  
  
 Skriptovací stroje používané na serverech se obvykle implementují jako objekty COM s volnými vlákny. To znamená, že metody rozhraní [IActiveScript](../winscript/reference/iactivescript.md) a jeho přidružená rozhraní mohou být volána z libovolného vlákna v procesu bez zařazování. (To bohužel také znamená, že skriptovací modul musí být implementován jako vnitroprocesové Server, protože technologie OLE v současné době nepodporuje zařazování objektů s volnými vlákny do procesů.) Na synchronizaci je zodpovědný skriptovací stroj. U skriptovacích strojů, které nejsou interně předané, nebo u jazykových modelů, které nejsou vícevláknové, by synchronizace mohla být jednoduchá jako serializace přístupu ke skriptovacímu modulu s objektem mutex. Některé metody, jako například [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), by neměly být tímto způsobem serializovány, takže zablokované skripty lze ukončit z jiného vlákna.  
  
 Skutečnost, že [IActiveScript](../winscript/reference/iactivescript.md) je obvykle volná vlákna, obvykle znamená, že rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) a objektový model hostitele by měly být také volné vlákny. To by vedlo k tomu, že implementace hostitele je poměrně obtížná, zejména v běžném případě, kdy je hostitelem aplikace pro Windows s jedním vláknem nebo ovládacími prvky ActiveX modelu apartment v jeho objektovém modelu. Z tohoto důvodu se na použití [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)skriptovacího modulu umístí následující omezení:  
  
 Skriptovací lokalita je vždy volána v kontextu hostitelského vlákna. To znamená, že skriptovací stroj nikdy nevolá lokalitu skriptu v kontextu vlákna, které vytvořil skriptovací modul, ale jenom z metody skriptovacího stroje, která byla volána od hostitele až po [IActiveScript](../winscript/reference/iactivescript.md) , a jeho derivátů, prostřednictvím vystaveného objektu pro odeslání skriptovacího modulu prostřednictvím zprávy systému Windows nebo ze zdroje události v objektovém modelu hostitele.  
  
 Skriptovací web není nikdy volán z kontextu jednoduché metody řízení stavu vlákna (například metoda [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) ) nebo z metody [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md) .  
  
## <a name="see-also"></a>Viz také  
 [Skriptovací rozhraní systému Windows](../winscript/windows-script-interfaces.md)
