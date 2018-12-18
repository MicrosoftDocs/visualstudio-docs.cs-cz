---
title: Obecné, ladění, dialogové okno Možnosti | Dokumentace Microsoftu
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
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3a9e0b8008da5b648ae156235a20964fc0952b1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742771"
---
# <a name="general-debugging-options-dialog-box"></a>Obecné, ladění, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nástroje / Možnosti / ladění / Obecné** stránka umožňuje nastavit následující možnosti:  
  
 **Zeptat se před smazáním všech zarážek**  
 Vyžaduje potvrzení před dokončením **smazat všechny zarážky** příkazu.  
  
 **Přerušit všechny procesy při přerušení jednoho procesu**  
 Současně ukončí všechny procesy, ke kterým je připojen ladicí program, když dojde k přerušení.  
  
 **Přerušit, pokud výjimky kříží třídu AppDomain nebo spravované/nativní hranice**  
 Ve spravovaném nebo kombinovaném režimu ladění, může modul CLR zachytit výjimky, které překračují hranice aplikační domény nebo spravované/nativní hranice, pokud jsou splněny následující podmínky:  
  
 1\) když nativní kód volá spravovaný kód pomocí zprostředkovatele komunikace s objekty COM a spravovaný kód vyvolá výjimku. Zobrazit [představení zprostředkovatele komunikace s objekty COM](http://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2\) když spravovaný kód spuštěný v aplikační doméně 1 volá spravovaný kód v aplikační doméně 2, a vyvolá výjimku, kód v aplikační doméně 2. Zobrazit [programování pomocí domén aplikace](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) když kód volá funkci pomocí reflexe a funkce vyvolá výjimku. Zobrazit [reflexe](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 V 2) a 3), je výjimka někdy zachycena spravovaným kódem v `mscorlib` místo modul common language runtime. Tato možnost nemá vliv na zastavení při výjimkách zachycených podle `mscorlib`.  
  
 **Povolit ladění na úrovni adres**  
 Umožňuje používat pokročilé funkce pro ladění na úrovni adresy ( **zpětný překlad** okně **zaregistruje** okna a zarážky adresy).  
  
 **Zobrazit zpětný překlad, pokud není k dispozici zdroj**  
 Automaticky zobrazí **zpětný překlad** okno při pokusu o ladění kódu pro zdroj, který je k dispozici.  
  
 **Povolit filtry zarážek**  
 Umožňuje nastavit filtry zarážky tak, že se ovlivní pouze specifické procesy, vlákna nebo počítače.  
  
 **Povolit Pomocníka pro výjimky**  
 Pouze pro spravovaný kód. Spravované výjimky otevřít dialogové okno pomocníka výjimky.  Zobrazit [pomocníka pro výjimky](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Vrátit zásobník volání v případě neošetřených výjimek**  
 Způsobí, že **zásobník volání** okno vrátit zásobník volání do bodu předtím, než došlo k neošetřené výjimce.  
  
 **Povolit volbu pouze vlastní kód**  
 Ladicí program zobrazí a vstoupí do uživatelského kódu ("můj kód") pouze, ignoruje systémový kód a jiný kód, který je optimalizován nebo který nemá žádné symboly ladění.  
  
 **Zobrazit všechny členy pro objekty jiných uživatelů v oknech proměnných (pouze Visual Basic)**  
 Zapne zobrazení neveřejných členů v objektech, které jsou v neuživatelském kódu (ne "můj kód").  
  
 **Varovat při žádném uživatelském kódu při spuštění**  
 Když ladění začíná s povolena funkce pouze můj kód, tato možnost vás upozorní, pokud neexistuje žádný uživatelský kód ("můj kód").  
  
 **.NET Framework, povolit krokování zdrojových kódů**  
 Umožňuje ladicímu programu vstup do zdroje rozhraní.NET Framework. Povolením této možnosti automaticky zakážete pouze můj kód rozhraní .NET Framework symboly budou staženy do umístění mezipaměti. Můžete změnit umístění mezipaměti v **možnosti** dialogovém okně **ladění** kategorie, **symboly** stránky.  
  
 **Krokovat přes vlastnosti a operátory (pouze spravované)**  
 Ladicí program zabraňuje krokování s vnořením do vlastností a operátorů ve spravovaném kódu.  
  
 **Povolit vyhodnocování vlastností a jiných implicitních volání funkcí**  
 Zapne automatické hodnocení vlastností a implicitní funkce se volá v oknech proměnných a **QuickWatch** dialogové okno.  
  
 **Volání funkce pro převod řetězce na objektech v oknech proměnné (C# a pouze pro jazyk JavaScript)**  
 Provede volání rozhraní řetězec implicitní převod při vyhodnocování objektů v oknech proměnných. Proto je výsledek zobrazen jako řetězec namísto názvu typu. Platí pouze při ladění v kódu jazyka C#. Toto nastavení lze přepsat pomocí atributu DebuggerDisplay (viz [pomocí atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Povolit podporu zdrojového serveru**  
 Sdělí ladicímu programu sady Visual Studio, aby získal zdrojové soubory ze zdrojových serverů, které implementují SrcSrv (`srcsrv.dll`) protokolu. Team Foundation Server a ladění nástroje pro Windows jsou dva servery zdroje, které implementují protokol. Další informace o nastavení SrcSrv naleznete v dokumentaci k ladění nástroje pro Windows. Kromě toho najdete v článku [zadejte symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Protože čtení souborů PDB může spustit libovolný kód v souborech, ujistěte se, že serveru důvěřujete.  
  
 **Vytisknout diagnostickou zprávu zdrojového serveru do okna výstup**  
 Pokud je povolena podpora zdrojového serveru, toto nastavení zapne diagnostické zobrazení.  
  
 **Povolit zdrojový server pro sestavení částečné důvěryhodnosti (pouze spravované)**  
 Pokud je povolena podpora zdrojového serveru, toto nastavení potlačí výchozí chování nenačítání zdrojů pro sestavení částečné důvěryhodnosti.  
  
 **Zvýraznění celého řádku pro zarážky a aktuální příkaz**  
 Pokud ladicí program zvýrazní zarážku nebo aktuální příkaz, jde zvýraznit celý řádek.  
  
 **Vyžadovat zdrojové soubory přesně shodovaly s originály**  
 Dává pokyn ladicímu programu k ověření, že zdrojový soubor odpovídá verzi zdrojového kódu k sestavení spustitelného souboru, který ladíte. Pokud verze neodpovídá, budete vyzváni k vyhledání odpovídajícího zdroje. Pokud není nalezen odpovídající zdroj, zdrojový kód se nezobrazí během ladění.  
  
 **Přesměrovat text z okna výstup do příkazového podokna**  
 Odešle všechny zprávy, které by se obvykle zobrazily v ladicího programu **výstup** okna **okamžité** okno místo.  
  
 **Zobrazit nezpracovanou strukturu objektů v oknech proměnných.**  
 Vypne všechny úpravy zobrazení struktury objektu. Další informace o přizpůsobení zobrazení naleznete v tématu [vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Potlačení optimalizace JIT při načtení modulu (pouze spravované)**  
 Zakáže optimalizaci JIT spravovaného kódu, když je modul je načten a JIT je zkompilován, zatímco je připojen ladicí program. Zakázání optimalizace může usnadnit práci ladění některých problémů, i když za cenu výkonu. Pokud používáte pouze můj kód, potlačení JIT optimalizace může způsobit kódu nepocházejícího od uživatele jako uživatelského kódu ("můj kód").  
  
 **Varovat, pokud žádné symboly při spuštění (pouze nativní)**  
 Zobrazí dialogové okno upozornění při pokusu o ladění programu, pro které ladicí program neobsahuje žádné informace o symbolu.  
  
 **Varovat, pokud je při spuštění zakázáno ladění skriptu**  
 Zobrazí dialogové okno upozornění, když ladicí program se spustí s ladění skriptů zakázáno.  
  
 **Načtení exportů dll**  
 Načte tabulky exportu knihovny dll. Informace o symbolech z tabulky exportu knihovny dll může být užitečné při práci s Windows zprávy, postupů Windows (WindowProcs), objekty COM nebo zařazování nebo libovolnou knihovnou dll pro kterou nemáte symboly. Informace o exportu knihovny dll pro čtení zahrnují nadměrné. Proto tato možnost je ve výchozím nastavení vypnuta.  
  
 Chcete-li zjistit, jaké symboly jsou k dispozici v exportní tabulce knihovny DLL, použijte `dumpbin /exports`. Symboly jsou k dispozici pro všechny 32bitové verzi systému dll. V článku `dumpbin /exports` výstupu uvidíte přesný název funkce, včetně jiných než alfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulky exportu knihovny dll může zobrazit ořezané jinde v ladicím programu. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace najdete v tématu [dumpbin/EXPORTS](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Zobrazit diagram paralelních zásobníků zdola nahoru**  
 Určuje směr, ve kterém jsou zobrazeny balíčky v **paralelní zásobníky** okna.  
  
 **Ignorovat výjimky přístupu k paměti GPU, pokud zapsaná data nezměnila hodnotu**  
 Ignoruje konflikty časování, které byly zjištěny během ladění, pokud se data nezměnila. Další informace najdete v tématu [ladění kódu GPU](../debugger/debugging-gpu-code.md).  
  
 **Použít spravovaný režim kompatibility**  
 Nahradí výchozí modul ladění pomocí starší verze, chcete-li povolit tyto scénáře:  
  
- Používáte jazyk rozhraní .NET Framework než C#, VB, nebo F# , který obsahuje vlastní vyhodnocení výrazu (to zahrnuje C + +/ CLI).  
  
- Chcete povolit funkce upravit a pokračovat pro projekty v jazyce C++ při ladění ve smíšeném režimu.  
  
  Všimněte si, že zvolíte kompatibility spravovaného režimu zakáže některé funkce, které jsou implementovány pouze ve výchozím ladicím modulu.  
  
  **Použít režim kompatibility nativní**  
  Pokud je vybraná tato možnost, ladicí program používá nativní ladicí program sady Visual Studio 2010 místo nové nativní ladicí program.  
  
  Tuto možnost by měla používat při ladění kódu .NET, C++, protože nového modulu pro ladění nepodporuje vyhodnocování výrazů .NET C++. Povolení nativní režim kompatibility zakáže však řadu funkcí, které závisí na aktuální implementace ladicí program k provozu. Například starý modul nemá mnoho vizualizéry pro předdefinované typy, jako jsou `std::string` v projektech Visual Studio 2015.   Chcete zajistit optimální práci ladění v těchto případech použijte projektů Visual Studio 2013.  
  
  **Použít starší verze vyhodnocovače výrazů C# a VB**  
  Ladicí program použije vyhodnocovače výrazů Visual Studio 2013 C# /VB místo vyhodnocovače výrazů Visual Studio 2015 roslynu.  
  
  **Upozornit při opakovaném použití vlastních vizualizérů ladění s potenciálně nebezpečnými procesy (pouze spravované)**  
  Visual Studio vás upozorní, když používáte vlastní vizualizér, na kterém běží kód v procesu laděného procesu, protože by mohl být spuštěn nebezpečný kód.  
  
  **Povolit přidělování haldy při ladění Windows (pouze nativní)**  
  Umožňuje haldy ladění systému windows k vylepšení diagnostiky haldy. Povolením této možnosti bude mít vliv na výkon ladění.  
  
  **Povolit ladění uživatelských rozhraní nástroje pro XAML**  
  Live Visual Tree a Live prozkoumejte vlastnost windows se zobrazí při spuštění ladění (F5) typ projektu podporovaná. Další informace najdete v tématu [vlastnosti kontrolovat XAML při ladění](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Zobrazit náhled vybraných elementů v dynamickém vizuálním stromu**  
  Prvek XAML, jehož kontext je vybraná také vybraný v **Live Visual Tree** okna.  
  
  **Zobrazit nástroje runtime v aplikaci**  
  Ukazuje, **Live Visual Tree** příkazy na panelu nástrojů v hlavním okně aplikace XAML, která je právě laděna. Tato možnost byla zavedena v aplikaci Visual Studio 2015 Update 2.  
  
  **Při ladění povolit diagnostické nástroje**  
  **Diagnostické nástroje** při ladění, zobrazí se okno. Další informace najdete v tématu [integrované v ladicím programu profilace](http://msdn.microsoft.com/library/a1f40370-7b61-42c2-afc4-0e13eba98859).  
  
  **Zobrazit časem, který uplynul při ladění**  
  V okně kódu zobrazí uplynulý čas dané metody volání při ladění.  
  
  **Povolit operaci upravit a pokračovat**  
  Můžete použít upravit a pokračovat funkce při ladění.  
  
  **Povolit nativní upravit a pokračovat**  
  Můžete použít upravit a pokračovat funkce při ladění nativního kódu C++. Další informace najdete v tématu [upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Použít změny při pokračování (jenom nativní)**  
  Visual Studio automaticky zkompiluje a použije změny nezpracovaných kódu, které jste provedli, když budete pokračovat procesu ze stavu pozastavení. Pokud není vybrána, můžete použít změny pomocí položky "Použít změny kódu" v nabídce ladění.  
  
  **Upozornit na starý kód (pouze nativní)**  
  Získáte upozornění na starý kód.  
  
  **Povolit předkompilování (pouze nativní)**  
  Předkompilace je povolen.  
  
## <a name="see-also"></a>Viz také  
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)



