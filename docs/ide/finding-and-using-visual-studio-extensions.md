---
title: Vyhledání a používání rozšíření
ms.date: 06/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc67602db2d830283bb47fe7c3a9728d0d9fd799
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067904"
---
# <a name="find-and-use-visual-studio-extensions"></a>Vyhledání a používání rozšíření sady Visual Studio

Rozšíření sady Visual Studio jsou balíčky kódu, které v prostředí Visual Studio a které poskytují nové nebo vylepšené funkce aplikace Visual Studio. Můžete najít další informace o rozšíření sady Visual Studio tady: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Můžete použít **rozšíření a aktualizace** dialogové okno instalace rozšíření sady Visual Studio a ukázky z webů a dalších míst a pak povolit, zakázat, aktualizovat nebo je odinstalovat. (**Nástroje > rozšíření a aktualizace**, nebo typ **rozšíření** v **Snadné spuštění** okno). Dialogové okno zobrazuje také aktualizace nainstalovaných ukázek a rozšíření. Můžete také stáhnout rozšíření z webů nebo získat od jiných vývojářů.

> [!NOTE]
> Spouští se v sadě Visual Studio 2015, rozšíření hostován aplikací Visual Studio Marketplace se automaticky aktualizují. Toto nastavení můžete změnit **rozšíření a aktualizace** dialogového okna.  Naleznete v části **automatické aktualizace rozšíření** níže podrobnosti.

## <a name="finding-visual-studio-extensions"></a>Vyhledání rozšíření sady Visual Studio

Můžete nainstalovat rozšíření z [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozšíření mohou být ovládací prvky, ukázky, šablony, nástroje nebo jiné součásti, které přidávají funkcionalitu do aplikace Visual Studio. Visual Studio podporuje rozšíření ve formátu balíčku VSIX – to zahrnuje šablony projektu, šablony položek, položky **nástrojů** položky, komponenty spravovaných rozšíření Framework (MEF) a rozšíření VSPackages. Můžete také stáhnout a nainstalovat rozšíření založená na Instalační služby MSI, ale **rozšíření a aktualizace** dialogové okno nelze povolit ani zakázat. Visual Studio Marketplace obsahuje rozšíření VSIX a instalační služby MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalace nebo odinstalace rozšíření sady Visual Studio

V **rozšíření a aktualizace**, najít rozšíření, které chcete nainstalovat. (Pokud znáte název nebo část názvu rozšíření, je možné hledat **hledání** okna.) Klikněte na tlačítko **Stáhnout**.  Rozšíření se naplánovaná instalace. Rozšíření se nainstaluje, když jsou uzavřeny všechny instance sady Visual Studio.

Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud tyto produkty nejsou nainstalovány, **rozšíření a aktualizace** dialogové okno obsahuje závislosti, které je třeba nainstalovat před instalací rozšíření.

Pokud chcete přestat používat rozšíření, lze jej zakázat nebo odinstalovat. Zakázáním rozšíření zůstane rozšíření nainstalováno, ale nedojde k jeho načtení. Můžete zakázat pouze rozšíření VSIX; rozšíření, které jsou nainstalované s použitím Instalační služba MSI lze pouze odinstalovat. Najít rozšíření a klikněte na tlačítko **odinstalovat** nebo **zakázat**. Aby bylo možné uvolnění zakázaného rozšíření je nutné restartovat Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Za uživatele a administrativní rozšíření

Většina rozšíření jsou rozšíření vázaná na uživatele a jsou nainstalovaná v *%LocalAppData%\Microsoft\VisualStudio\\< verze sady Visual Studio\>\Extensions\\*  složky. Několik rozšíření jsou administrativní rozšíření a jsou nainstalovaná v *\<instalační složky sady Visual Studio > \Common7\IDE\Extensions\\* složky.

Pro ochranu systému proti rozšíření, které mohou obsahovat chyby nebo škodlivý kód, můžete omezit rozšíření vázaná na uživatele pro načtení pouze při spuštění sady Visual Studio s oprávněními běžných uživatelů. To znamená, že je zakázáno rozšíření vázaná na uživatele, při spuštění sady Visual Studio s oprávněními správce. Chcete-li to provést, přejděte na **rozšíření a aktualizace** stránka možností (**nástroje > Možnosti** > **prostředí** > **rozšíření a aktualizace**, nebo zadejte **rozšíření** v **Snadné spuštění** okno). Zrušte **načítání rozšíření pro jednotlivé uživatele při spuštění jako správce** zaškrtněte políčko a potom restartujte Visual Studio.

## <a name="automatic-extension-updates"></a>Aktualizace automatické rozšíření

Rozšíření vázaná na uživatele se automaticky aktualizují, když je nová verze pro Visual Studio Marketplace.  Nová verze rozšíření rozpoznán a nainstalován na pozadí a při příštím restartování sady Visual Studio, používat novou verzi rozšíření.

Jen rozšíření vázaná na uživatele je možné automaticky aktualizovat.  Administrativní rozšíření, která jsou nainstalována pro všechny uživatele, neaktualizuje se a ručně nainstalujte nové verze prostřednictvím **rozšíření a aktualizace** dialogového okna **aktualizace** uzlu. Uvidíte, jaká rozšíření se automaticky aktualizují v podokně podrobností rozšíření **rozšíření a aktualizace** dialogového okna.

Pokud chcete zakázat automatické aktualizace, můžete zakázat funkci pro všechny přípony nebo pouze konkrétní rozšíření.

- Chcete-li zakázat automatické aktualizace pro všechna rozšíření, zvolte **změnit nastavení rozšíření a aktualizace** odkaz v **rozšíření a aktualizace** dialogové okno a zrušte zaškrtnutí políčka **automaticky aktualizovat. rozšíření**.

- Chcete-li zakázat automatické aktualizace pro konkrétní příponu, zrušte zaškrtnutí políčka **automaticky aktualizovat toto rozšíření** možnost v podokně podrobností rozšíření na pravé straně **rozšíření a aktualizace** dialogového okna.

> [!NOTE]
> Od verze Visual Studio 2015 Update 2, můžete zadat (v **nástroje > Možnosti > prostředí > rozšíření a aktualizace**) určuje, zda chcete automatické aktualizace pro rozšíření vázaná na uživatele, všechna rozšíření uživatele nebo obě (výchozí nastavení nastavení).

## <a name="extension-crashunresponsiveness-notifications"></a>Oznámení rozšíření zhroucení nebo zablokování

Novinka v **Visual Studio 2017 verze 15.3**, Visual Studio vás upozorní, pokud má podezření, že rozšíření byl zahrnut v chybě během předchozí relace. Pokud dojde k chybě sady Visual Studio, ukládá zásobník výjimek. Při příštím spuštění Visual Studio zjistí zásobníku, počínaje listu a funguje směrem k základní třídě. Pokud Visual Studio zjistí, že blok patří do modulu, který je součástí rozšíření nainstalované a povolené, zobrazuje oznámení o.

Novinka v **Visual Studio 2017 verze 15.6**, Visual Studio také vás upozorní, pokud způsobuje, že rozšíření uživatelského rozhraní za nereagujícího.

Když tato oznámení jsou zobrazeny, můžete ignorovat oznámení nebo Absolvujte některou z následujících akcí:

- Zvolte **zakázat toto rozšíření**. Visual Studio zakáže rozšíření a poznáte, jestli je potřeba restartovat systém pro zakázání se projeví. Můžete znovu povolit doplněk **rozšíření a aktualizace** dialogovému oknu, chcete-li.

- Zvolte **tuto zprávu již nezobrazovat**.
  - Pokud oznámení týká chybovému ukončení v předchozí relaci, Visual Studio nebude zobrazovat, že dojde k oznámení, když se chyby spojené s touto příponou. Visual Studio bude stále zobrazovat upozornění při zablokování můžou být spojené s touto příponou nebo zhroucení nebo zablokování, která můžou být spojené s další rozšíření.
  - Pokud oznámení se týká sekundový výpadek reakce, integrovaném vývojovém prostředí už zobrazit oznámení, když toto rozšíření je přidružen sekundový výpadek reakce. Visual Studio se stále zobrazí oznámení týkající se chyb pro tuto příponu a při selhání a zablokování související upozornění pro další rozšíření.

- Zvolte **Další** na této stránce.

- Zvolte **X** tlačítko na konci oznámení zavřete oznámení. Zobrazí se nové oznámení pro budoucí instance rozšíření jsou spojeny s zhroucení nebo zablokování uživatelského rozhraní.

> [!NOTE]
> Uživatelské rozhraní sekundový výpadek reakce nebo selhání oznámení znamená, že pouze jeden z tohoto rozšíření modulů v zásobníku byl při reagovat uživatelské rozhraní, nebo když došlo k selhání. To neznamená, že rozšíření samotné bylo nadměrné spotřeby. Je možné, že rozšíření volat kód, který je součástí sady Visual Studio, které zase přestal reagovat uživatelské rozhraní nebo selhání. Však oznámení může být stále užitečná, pokud rozšíření, která vedla k zablokování uživatelského rozhraní nebo při selhání není pro vás důležité. V takovém případě při zakázání rozšíření zabráněno zablokování uživatelského rozhraní nebo selhání v budoucnu, bez dopadu na vaši produktivitu.

## <a name="sample-master-copies-and-working-copies"></a>Ukázka hlavní kopie a pracovní kopie

Při instalaci online ukázky je řešení uloženo na dvou místech:

- Pracovní kopie je uložena v umístění, které jste zadali v **nový projekt** dialogové okno.

- Samostatná hlavní kopie je uložena v počítači.

Můžete použít **rozšíření a aktualizace** dialogové okno k provedení těchto úloh týkajících se ukázek:

- Zobrazit seznam hlavních kopií ukázek, které jste nainstalovali.

- Zakázat nebo odinstalovat hlavní kopii ukázky.

- Instalovat balíky ukázek, což jsou kolekce ukázek, které se týkají technologie nebo funkce.

- Nainstalujte jednotlivé online ukázky. (Můžete to provést také v **nový projekt** dialogové okno.)

- Zobrazit upozornění na aktualizace při zveřejnění změny zdrojového kódu nainstalovaných ukázek.

- Aktualizujte hlavní kopii nainstalované ukázky, když je oznámení o aktualizaci.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalace bez použití dialogovém okně rozšíření a aktualizace

Rozšíření, která byla zabalena v souboru *VSIX* soubory mohou být k dispozici v jiném umístění než Visual Studio Marketplace. **Rozšíření a aktualizace** dialogové okno nelze rozpoznat tyto soubory, ale můžete nainstalovat *VSIX* soubor poklikáte soubor nebo výběr souboru a stisknutím klávesy **Enter**klíč. Potom postupujte podle pokynů. Pokud je rozšíření nainstalované, můžete použít **rozšíření a aktualizace** dialogové okno povolit, zakázat nebo ho odinstalujte.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Rozšíření typy nejsou podporovány v dialogovém okně rozšíření a aktualizace

Visual Studio i nadále podporuje rozšíření, které instaluje Microsoft Installer (MSI) ale není až **rozšíření a aktualizace** dialogové okno bez úprav.

> [!TIP]
> Pokud obsahuje rozšíření na základě Instalační služby MSI *extension.vsixmanifest* soubor rozšíření se zobrazí v **rozšíření a aktualizace** dialogové okno.