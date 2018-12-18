---
title: Skriptovací stroje systému Windows | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16e699ee789ae10883152b5d8aa7d8ffee0ddffd
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572618"
---
# <a name="windows-script-engines"></a>Skriptovací stroje systému Windows
Pokud chcete implementovat modul Microsoft Windows skript, vytvořte objekt OLE COM, který podporuje následující rozhraní.  
  
|||  
|-|-|  
|Rozhraní|Popis|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Poskytuje základní možnosti skriptování. Implementace tohoto rozhraní je povinný.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Umožňuje přidat text skriptu, vyhodnocení výrazů a tak dále. Implementace tohoto rozhraní je volitelná. ale pokud není implementovaný, skriptovací stroj musí implementovat jednomu z rozhraní IPersist * Chcete-li načíst skript.|  
|IPersist *|Poskytuje podporu trvalost. Implementace nejméně jedné z následujících rozhraní je povinný, pokud [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) není implementována.<br /><br /> IPersistStorage: Poskytuje podporu pro DATA = {url} atribut ve značce OBJECT.<br /><br /> IPersistStreamInit: Poskytuje podporu pro stejný jako `IPersistStorage` a také DATA = "datového proudu bajtů kódovaný řetězec" atribut ve značce OBJECT.<br /><br /> IPersistPropertyBag: Poskytuje podporu pro se parametr = atribut ve značce OBJECT.|  
  
> [!NOTE]
>  Je možné, že skriptovací stroj nebude nikdy volat při uložení nebo obnovení stavu skriptu prostřednictvím `IPersist*`. Místo toho [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) se používá při volání [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) vytvořit prázdnou skript, pak Skriptlety jsou přidány a připojený k události s [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) a obecné kódu se přidá s [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Skriptovací stroj musí však plně implementovat alespoň jeden `IPersist*` rozhraní (pokud možno `IPersistStreamInit`), protože jiné aplikace hostitele může pokusí provést pomocí z nich.  
  
 Následující části popisují implementaci modul Windows skriptování podrobněji.  
  
 Najdete v článku [referenční dokumentace skriptovacích rozhraní systému Windows](../winscript/reference/windows-script-interfaces-reference.md) Další informace.  
  
## <a name="registry-standard"></a>Standardní registru  
 Modul Windows Script můžete identifikovat pomocí identifikátorů kategorie. Modul Windows Script aktuálně definuje dva identifikátory kategorie.  
  
|||  
|-|-|  
|Kategorie|Popis|  
|CATID_ActiveScript|Označuje, že identifikátorů tříd (CLSID) jsou Windows skriptovacích strojů, které podporují minimálně [IActiveScript –](../winscript/reference/iactivescript.md) mechanismus trvalosti a rozhraní ( `IPersistStorage`, `IPersistStreamInit`, nebo IPersistPropertyBag rozhraní).|  
|CATID_ActiveScriptParse|Označuje, že jsou identifikátory CLSID Windows skriptovacích strojů, které podporují minimálně [IActiveScript –](../winscript/reference/iactivescript.md) a [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) rozhraní.|  
  
 I když [IActiveScriptParse –](../winscript/reference/iactivescriptparse.md) není mechanismus trvalosti true podporuje [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metoda, která je funkčně srovnatelný `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>Modul stavů skriptu  
 V každém okamžiku může být modul Windows Script v jednom z několika stavů.  
  
|||  
|-|-|  
|Stav|Popis|  
|Neinicializovaný|Skript nebyl inicializován nebo načíst pomocí rozhraní IPersist * nebo nemá [iactivescriptsite –](../winscript/reference/iactivescriptsite.md) rozhraní sady. Skriptovací stroje není obecně použitelné z tohoto stavu dokud je skript načten.|  
|inicializovat|Skript byl inicializován s `IPersist*` rozhraní a má [iactivescriptsite –](../winscript/reference/iactivescriptsite.md) rozhraní sady, ale není připojený k hostiteli objekty a vnořování události. Všimněte si, že tento stav jednoduše znamená, že `IPersist*::Load`, `IPersist*::InitNew`, nebo [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metoda byla dokončena a že [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) byla volána metoda. Modul nelze spustit kód v tomto režimu. Modul fronty kód, který hostitel předá přes [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) metoda a spouští kód po přechodu do spuštěného stavu.<br /><br /> Vzhledem k tomu jazyků můžete v sémantiku velmi lišit, nejsou skriptovacích strojů vyžadovaná pro podporu tento přechod stavu. Motory podporující [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) metoda musí, ale podporují tento přechod stavu. Hostitelé musí připravit pro tento přechod a proveďte příslušnou akci: vydání aktuální skriptovací stroje, vytvořte novou skriptovací stroj a volání `IPersist*::Load`, `IPersist*::InitNew`, nebo [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (a případně také zavolat [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). Použijte tento přechod měli zvážit optimalizaci výše uvedených kroků. Upozorňujeme, že všechny skriptovací stroj má získat informace o názvech položek s názvem a typ informace, které popisují položky s názvem zůstává v platnosti.<br /><br /> Protože jazyky velmi lišit, definování přesný sémantika tento přechod je obtížné. Minimálně musí skriptovacího stroje odpojte od všechny události a verze všech ukazatelů SCRIPTINFO_IUNKNOWN získá voláním [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) metoda. Po spuštění skriptu znovu, musíte modul znovu získat tyto ukazatele. Skriptovací stroj musí také obnovit skript počáteční stav, který je vhodný pro jazyk. Jazyk VBScript, například obnoví všechny proměnné a uchovává žádný kód dynamicky přidá se při volání [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) s SCRIPTTEXT_ISPERSISTENT nastaven příznak. Další jazyky chtít zachovat aktuální hodnoty (například Lisp, protože neexistuje žádný kód nebo data oddělení) nebo resetovat do dobře známého stavu (to zahrnuje jazyků s staticky inicializovaného proměnné).<br /><br /> Všimněte si, že přechodu do spuštěného stavu by měl mít stejnou sémantiku (to znamená, že ho nechat skriptovacího stroje v takovém stavu) jako volání `IPersist*::Save` uložte skriptovací stroje a pak volání `IPersist*::Load` načíst nový skriptovací stroj; tato akce by měly mít stejnou sémantiku jako [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). Skriptovací stroje, které zatím nepodporují `IActiveScript::Clone` nebo `IPersist*` zvažte chování přechodu do spuštěného stavu, takže tento přechod nebude porušují výše uvedených podmínek, pokud `IActiveScript::Clone` nebo `IPersist*` později byla přidána podpora.<br /><br /> Během tento přechod do stavu spuštěno skriptovacího stroje dojde k odpojení od jímky událostí po odpovídající destruktory a atd., jsou spouštěny ve skriptu. Chcete-li předejít tyto destruktory provést, hostiteli můžete nejprve přesunout skript v odpojeném stavu před přesunutím do spuštěného stavu.<br /><br /> Použití [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) zrušit běžící vlákna skript bez čekání na aktuální události a tak dále, při dokončení spuštění.|  
|spuštění|Přechod z inicializovaný stav spuštěného stavu způsobí, že modul provést kód, který byl zařazen do inicializovaný stav. Modul může spustit kód ve stavu spuštěna, ale není připojen k žádné události prostřednictvím přidány [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) metoda. Modul může spustit kód s voláním rozhraní IDispatch získaný [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) metody nebo voláním [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Je možné, že další pozadí inicializaci (progresivní načítání) dosud probíhá a že volání [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metoda nastaven příznak SCRIPTSTATE_CONNECTED může způsobit, že skript, který chcete zablokovat až do dokončení inicializace.|  
|připojení|Skript je načíst a připojení pro zpracování událostí z hostitele objektů. Pokud je přechod z inicializovaný stav, skriptovací stroj měli přechod prostřednictvím Začínáme stavu, provádění akce nezbytné, před zadáním stav připojení a připojení k události.|  
|odpojení|Skript je načteno a má stav běhu, ale je dočasně odpojen od vnořování události z hostitele objektů. To můžete provést buď logicky (ignorována událostí přijatých) nebo fyzicky (volání IConnectionPoint::Unadvise na příslušné spojovací body). Pokud je přechod z inicializovaný stav, skriptovací stroj měli přechod prostřednictvím Začínáme stavu, provádění akce nezbytné před vstupem odpojeném stavu. Jímky událostí, které jsou v průběhu dokončení před změny stavu (použijte [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) zrušit běžící vlákna skriptu). Tento stav je rozlišující z inicializovaný stav v že přechodu na tento stav nezpůsobí skript, který chcete obnovit, není-li obnovit stav běhu skriptu a inicializace procedury skript není proveden.|  
|uzavřený|Skript byl uzavřen. Skriptovací stroje už funguje a vrátí chyby pro většinu metod.|  
  
 Následující obrázek znázorňuje vztahy mezi různými skriptovací stroj státy a zobrazuje metody, které způsobí přechody z jednoho stavu do jiného.  
  
 Následující obrázek znázorňuje akce, které provádí skriptovací stroj při různých přechodů mezi stavy.  
  
## <a name="scripting-engine-threading"></a>Skriptovací stroje dělení na vlákna  
 Protože je možné použít modul Windows Script do mnoha prostředí, je důležité udržovat svůj model provádění co nejpružnější. Na serveru hostitele může například muset zachovat vícevláknové návrhu při použití skriptu Windows účinným způsobem. Ve stejnou dobu by neměl být hostitele, který nepoužívá dělení na vlákna, jako je například Typická aplikace burdened s dělení na vlákna správy. Skript Windows dosahuje toto vyrovnávání omezení způsoby, které podprocesy skriptovacího stroje můžete volat zpět na hostitele, uvolnění hostitele z této zatížení.  
  
 Skriptovacích strojů použít na servery jsou obvykle implementovány jako volné threading COM – objekty. To znamená, že v metody [IActiveScript –](../winscript/reference/iactivescript.md) rozhraní a jeho přidružené rozhraní lze volat z libovolného vlákna v procesu bez kódování. (Bohužel také to znamená, že skriptovacího stroje musí být implementována jako server v procesu, protože OLE nepodporuje aktuálně meziprocesová zařazování podprocesy objektů.) Synchronizace je zodpovědností skriptovacího stroje. Pro skriptovací stroje, které nejsou interně vícenásobné nebo pro jazyk modely, které nejsou s více vlákny může být stejně jednoduché jako serializaci přístup k modulu skriptování s mutex synchronizace. Samozřejmě některé metody, jako například [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), nesmí být serializován tímto způsobem, aby ukončovat lze zablokované skriptu z jiné vlákno.  
  
 Fakt, na který [IActiveScript –](../winscript/reference/iactivescript.md) je obvykle podprocesy obecně vyplývá, že [iactivescriptsite –](../winscript/reference/iactivescriptsite.md) rozhraní a objektového modelu hostitele by měla být podprocesy také. Implementace hostitele, mohou mít velmi obtížné, zejména v častých případech, kde hostitele je aplikace jednovláknové systému Windows s jedním podprocesem nebo apartment model ovládací prvky ActiveX v jeho objektový model. Z tohoto důvodu se umístí následující omezení použití skriptovací stroje [iactivescriptsite –](../winscript/reference/iactivescriptsite.md):  
  
 Skript lokality je volána vždy v kontextu vláken hostitele. To znamená, skriptování modul nikdy volání webu skriptu v kontextu vláken, která skriptovací stroj vytvořil, ale pouze z uvnitř skriptovací modul metoda, která byla volána z hostitele prostřednictvím [IActiveScript –](../winscript/reference/iactivescript.md) a odvozené, prostřednictvím objektu odesílání zveřejněné skriptovací stroje, prostřednictvím zpráv systému Windows nebo ze zdroje událostí v modelu objektu hostitele.  
  
 Lokality skriptu nikdy volat v rámci kontextu metody řízení stavu simple vlákno (například [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) metoda) nebo z [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) metoda.  
  
## <a name="see-also"></a>Viz také  
 [Skriptovací rozhraní systému Windows](../winscript/windows-script-interfaces.md)
