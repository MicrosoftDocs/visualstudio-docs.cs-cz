---
title: Sada pravidel dialogové okno Editor (starší verze) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 3469e395ee50e63f8ac76e4181d02b777ccbd4ba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942397"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Dialogové okno Editor sad pravidel (starší verze)
Toto téma popisuje, jak používat **editoru nastavte pravidlo** dialogové okno v starší [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] potřeba cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 **Editoru nastavte pravidlo** dialogové okno se používá k vytvoření a úprava [aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) pravidlo sady, které se serializují do souboru .rules.  
  
> [!NOTE]
>  Pokud chcete otevřít soubor .rules s **Editor XML s kódováním**, je zapotřebí nejdříve zavřít okno přidružené Návrháře pracovního postupu nebo aktivity.  
  
 Informace o tom, jak získat přístup k **editoru nastavte pravidlo** dialogovém okně naleznete v tématu [postupy: vytvoření aktivitě PolicyActivity sada pravidel (starší verze)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  Editor pravidel starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] cílit na platformu, která se používá [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] není podporováno cílení na více verzí.  
  
 Následující tabulka popisuje prvky uživatelského rozhraní (UI) **editoru nastavte pravidlo** dialogové okno.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Přidat pravidlo**|Přidá novou definici pravidlo do sady pravidel.|  
|**Delete**|Odstraní vybrané pravidlo ze sady pravidel.|  
|**Řetězení**|Určuje, jaký typ vpřed řetězení pomocí sady pravidel. Dostupné jsou následující možnosti:<br /><br /> -   **Úplné zřetězení**, která určuje použít všechny dopředné řetězení mechanismy: implicitní, metoda přidělování a explicitní použití **aktualizace** funkce.<br />-   **Sekvenční**, která určuje nepoužívat dopředné řetězení.<br />-   **Pouze explicitní aktualizace**, která určuje provádět jenom vpřed řetězení na **aktualizace** akce.<br /><br /> Další informace o přesměrování řetězení najdete v tématu [pomocí aktivity aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Jméno**|Sada pravidel seznamu záhlaví sloupce. Kliknutím seřadíte seznam pravidel podle názvu.|  
|**Priorita**|Sada pravidel seznamu záhlaví sloupce. Kliknutím seřadíte seznam pravidel podle priority.|  
|**Přehodnocení**|Sada pravidel seznamu záhlaví sloupce. Kliknutím seřadíte seznam podle typu opětovného hodnocení.|  
|**Náhled pravidla**|Sada pravidel seznamu záhlaví sloupce. Kliknutím seřadíte seznam pravidel ve verzi preview pravidlo podmínku a akce.|  
|**Jméno:**|Zadejte název pravidla.|  
|**Priorita:**|Zadejte pro pravidlo s prioritou. Výchozí priorita je 0.|  
|**Přehodnocení:**|Určuje, jaký typ nového vyhodnocení pravidla používat s tímto pravidlem. Dostupné jsou následující možnosti:<br /><br /> -   **Vždy**, což způsobí, že pravidlo se znovu vyhodnotit podle potřeby.<br />-   **Nikdy**, což způsobí, že nikdy se znovu vyhodnotit pravidla. V tomto případě pravidlo spustí pouze jednou.|  
|**Aktivní**|Zaškrtněte, pokud chcete aktivovat pravidlo.|  
|**Podmínka:**|Zadejte výraz pro podmínku pravidla. Informace o syntaxi výrazů najdete v části "Zadávání podmínku a akce výrazů" této stránky.|  
|**Potom akce:**|Zadejte výraz pro pak akce. Informace o syntaxi výrazů najdete v části "Zadávání podmínku a akce výrazů" této stránky.|  
|**Ostatní akce:**|Zadejte výraz Else akce. Informace o syntaxi výrazů najdete v části "Zadávání podmínku a akce výrazů" této stránky.|  
|**OK**|Klikněte na tlačítko Uložit do souboru .rules sadu pravidel.|  
  
 Další informace o sadě pravidel, naleznete v tématu [pomocí aktivity aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Zadání podmínky a akce výrazy  
 Zadejte výrazy pro podmínky a pak a jiná akce jako textu v jejich příslušných polích v **editoru nastavte pravidlo** dialogové okno. Můžete zadat **to.** v editoru odkazovat na pole, vlastnosti a metody použité v pracovním postupu pomocí typu IntelliSense nabídky. Můžete taky zadat název člena pracovního postupu přímo. Statické metody lze volat v odkazovaných typů tak, že zadáte název třídy následovaný názvem metody.  
  
 Logické operátory můžete přidat do podmínky, jako je například AND, OR a NOT. Můžete také přidat predikáty. Predikát je binárním operátorem a dva operandy. Jsou podporované binární operátory ==, >, \<, > =, a < =. Konstantní hodnota, aritmetické funkce a oboru veřejné členy jsou podporované operandy.  
  
 Můžete určit typ pro porovnání, a můžete porovnat s **null** nebo prázdný řetězec. Můžete vnořit volání členů na proměnnou, která obsahuje komplexní typ, třeba `this.Address.State == "WA"`.  
  
 Výrazy podporují následující operátory:  
  
- Relační operátory: ==, =,! =  
  
- Relační operátory: <, \<=, >, > =  
  
- Aritmetické operátory: +, -, *, /, MOD  
  
- Logické operátory: A, & &, OR, &#124; &#124;, ne,!  
  
- Bitové operátory: &&#124;  
  
  Priorita operátorů výraz následuje pravidla priorit operátor C#.  
  
  Další informace o podmínkách najdete v tématu [podmínky použití v pracovních postupech](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Zastavení a aktualizace funkcí  
 **Potom akce:** a **Else akce:** výrazy podporují **zastaví** a **aktualizace** funkce. Použít **zastaví** funkci, zadejte **Zastavit** do **pak akce:** nebo **Else akce:** textového pole. **Zastaví** akce způsobí spuštění sady pravidel se okamžitě zastavit a ovládací prvek vrátí volajícímu kódu. Můžete použít **aktualizace** funkce s vpřed řetězení.  
  
 **Aktualizace** příkaz může být vyjádřena v editoru v jednom z těchto dvou tvarů; obě formy jsou uvedeny v následujícím příkladu:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Další informace o používání **aktualizace** s řetězení vpřed, přečtěte si téma [pomocí aktivity aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Viz také  
 [Aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Dialogové okno nastavit vyberte pravidla (starší verze)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Pomocí aktivit zásad aktivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Pomocí podmínek v pracovních postupech](http://go.microsoft.com/fwlink?LinkID=65009)