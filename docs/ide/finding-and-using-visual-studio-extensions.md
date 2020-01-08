---
title: Hledání a instalace rozšíření
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f016af58b5799ca37b1a8f0cc54366d639c57c03
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594406"
---
# <a name="manage-extensions-for-visual-studio"></a>Správa rozšíření pro Visual Studio

Rozšíření jsou balíčky kódu, které se spouštějí v rámci sady Visual Studio a poskytují nové nebo vylepšené funkce. Rozšíření mohou být ovládací prvky, ukázky, šablony, nástroje nebo jiné komponenty, které přidávají funkce do sady Visual Studio, například [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) nebo [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Informace o vytváření rozšíření sady Visual Studio naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Informace o používání rozšíření najdete na stránce individuálního rozšíření na [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Dialogové okno rozšíření a aktualizace

Pomocí dialogového okna **rozšíření a aktualizace** můžete nainstalovat a spravovat rozšíření sady Visual Studio. Chcete-li otevřít dialogové okno **rozšíření a aktualizace** , vyberte možnost **nástroje** > **rozšíření a aktualizace**nebo **rozšíření** zadejte do vyhledávacího pole snadné **spuštění** .

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Dialogové okno Správa rozšíření

Pomocí dialogového okna **Spravovat rozšíření** můžete nainstalovat a spravovat rozšíření sady Visual Studio. Chcete-li otevřít dialogové okno **Spravovat rozšíření** , vyberte možnost **rozšíření** > **Spravovat rozšíření**. Případně zadejte do vyhledávacího pole **přípony** a klikněte na **Spravovat rozšíření**.

::: moniker-end

![Okno rozšíření v aplikaci Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Podokno v levé části kategorizace rozšíření podle těch, které jsou k dispozici na Visual Studio Marketplace (**online**) a u těch, které mají dostupné aktualizace. **Správce rozšíření pro roaming** uchovává seznam všech rozšíření sady Visual Studio, která jste nainstalovali na libovolný počítač nebo instanci sady Visual Studio. Je navržená tak, aby vám usnadnila hledání vašich oblíbených rozšíření.

## <a name="find-and-install-extensions"></a>Hledání a instalace rozšíření

::: moniker range="vs-2017"

Rozšíření můžete nainstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com) nebo dialogového okna rozšíření a aktualizace v aplikaci Visual Studio.

Instalace rozšíření z aplikace Visual Studio:

1. V části **nástroje** > **rozšíření a aktualizace**Najděte rozšíření, které chcete nainstalovat. Pokud znáte název nebo část názvu rozšíření, můžete hledat v okně **hledání** .

2. Vyberte **Download** (Stáhnout).

   U rozšíření je naplánovaná instalace. Vaše rozšíření se nainstaluje po uzavření všech instancí sady Visual Studio.

Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud tyto produkty nejsou nainstalovány, **rozšíření a aktualizace** dialogové okno obsahuje závislosti, které je třeba nainstalovat před instalací rozšíření.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Instalace bez použití dialogového okna rozšíření a aktualizace

Rozšíření, která byla zabalena v souborech *. vsix* , mohou být k dispozici v jiných umístěních než Visual Studio Marketplace. V dialogovém okně **nástroje** > **rozšíření a aktualizace** nelze rozpoznat tyto soubory, ale můžete nainstalovat soubor *. vsix* dvojitým kliknutím na soubor nebo výběrem souboru a stisknutím klávesy **ENTER**. Potom postupujte podle pokynů. Pokud je rozšíření nainstalované, můžete použít **rozšíření a aktualizace** dialogové okno povolit, zakázat nebo ho odinstalujte.

> [!NOTE]
> - Visual Studio Marketplace obsahuje rozšíření VSIX i MSI. Dialogové okno rozšíření a aktualizace nemůže povolit ani zakázat rozšíření založená na MSI.
> - Pokud rozšíření založené na MSI obsahuje soubor *extension. vsixmanifest* , rozšíření se zobrazí v dialogovém okně **rozšíření a aktualizace** .

::: moniker-end

::: moniker range=">=vs-2019"

Rozšíření můžete nainstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com) nebo dialogového okna spravovat rozšíření v aplikaci Visual Studio.

Instalace rozšíření z aplikace Visual Studio:

1. V části **rozšíření** > **Správa rozšíření**Najděte rozšíření, které chcete nainstalovat. (Pokud znáte název nebo část názvu rozšíření, je možné hledat **hledání** okna.)

2. Vyberte **Download** (Stáhnout).

   U rozšíření je naplánovaná instalace. Vaše rozšíření se nainstaluje po uzavření všech instancí sady Visual Studio.

Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud nejsou nainstalované, dialogové okno **Spravovat rozšíření** zobrazí seznam závislostí, které je třeba nainstalovat, než bude možné nainstalovat rozšíření.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Instalace bez použití dialogového okna spravovat rozšíření

Rozšíření, která byla zabalena v souborech *. vsix* , mohou být k dispozici v jiných umístěních než Visual Studio Marketplace. Dialogové okno **rozšíření** > **Spravovat rozšíření** nedokáže rozpoznat tyto soubory, ale můžete nainstalovat soubor *. vsix* dvojitým kliknutím na soubor nebo vybráním souboru a stisknutím klávesy **ENTER**. Potom postupujte podle pokynů. Když je rozšíření nainstalované, můžete ho pomocí dialogového okna **Spravovat rozšíření** povolit, zakázat nebo odinstalovat.

> [!NOTE]
> - Visual Studio Marketplace obsahuje rozšíření VSIX i MSI. Dialogové okno Spravovat rozšíření nemůže povolit ani zakázat rozšíření založená na MSI.
> - Pokud rozšíření založené na MSI obsahuje soubor *extension. vsixmanifest* , rozšíření se zobrazí v dialogovém okně **Spravovat rozšíření** .

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Odinstalovat nebo zakázat rozšíření

Pokud chcete přestat používat rozšíření, lze jej zakázat nebo odinstalovat. Zakázáním rozšíření zůstane rozšíření nainstalováno, ale nedojde k jeho načtení. Najít rozšíření a klikněte na tlačítko **odinstalovat** nebo **zakázat**. Restartováním sady Visual Studio uvolněte zakázané rozšíření.

> [!NOTE]
> Můžete zakázat rozšíření VSIX, ale ne rozšíření, která byla nainstalována pomocí MSI. Rozšíření instalovaná prostřednictvím MSI se dají odinstalovat jenom.

## <a name="per-user-and-administrative-extensions"></a>Za uživatele a administrativní rozšíření

Většina rozšíření je vázaná na uživatele a je instalována ve složce *%LocalAppData%\Microsoft\VisualStudio\\\\složce sady Visual Studio\>\Extensions* . Některá rozšíření jsou rozšíření pro správu a jsou nainstalována ve složce *\<instalační složka sady Visual Studio > složce \Common7\IDE\Extensions\\* .

Pro ochranu systému proti rozšíření, které mohou obsahovat chyby nebo škodlivý kód, můžete omezit rozšíření vázaná na uživatele pro načtení pouze při spuštění sady Visual Studio s oprávněními běžných uživatelů. To znamená, že rozšíření vázaná na uživatele jsou zakázána při spuštění sady Visual Studio se zvýšenými oprávněními.

Omezení načtení rozšíření pro jednotlivé uživatele:

1. Otevřete stránku možnosti rozšíření (**nástroje** > **Možnosti** >  > **rozšíření** **prostředí** ).

2. Zrušte zaškrtnutí políčka **načíst rozšíření pro jednotlivé uživatele při spuštění jako správce** .

3. Restartujte sadu Visual Studio.

## <a name="automatic-extension-updates"></a>Aktualizace automatické rozšíření

Rozšíření se automaticky aktualizují, když je na Visual Studio Marketplace k dispozici nová verze. Nová verze rozšíření se zjistí a nainstaluje na pozadí. Při příštím spuštění aplikace Visual Studio bude spuštěna nová verze rozšíření.

Pokud chcete zakázat automatické aktualizace, můžete tuto funkci zakázat pro všechna rozšíření nebo jenom pro konkrétní rozšíření.

::: moniker range="vs-2017"

- Chcete-li zakázat automatické aktualizace pro všechna rozšíření, klikněte na odkaz **změnit nastavení rozšíření a aktualizace** v dialogovém okně **nástroje** > **rozšíření a aktualizace** . V dialogovém okně **Možnosti** zrušte možnost **automaticky aktualizovat rozšíření**.

- Chcete-li zakázat automatické aktualizace pro konkrétní příponu, zrušte zaškrtnutí políčka **automaticky aktualizovat toto rozšíření** možnost v podokně podrobností rozšíření na pravé straně **rozšíření a aktualizace** dialogového okna.

::: moniker-end

::: moniker range=">=vs-2019"

- Chcete-li zakázat automatické aktualizace pro všechna rozšíření, klikněte na odkaz **změnit nastavení pro rozšíření** v dialogovém okně **rozšíření** > **Spravovat rozšíření** . V dialogovém okně **Možnosti** zrušte možnost **automaticky aktualizovat rozšíření**.

- Chcete-li zakázat automatické aktualizace konkrétního rozšíření, zrušte v podokně podrobností rozšíření na pravé straně dialogového okna **Spravovat rozšíření** možnost **automaticky aktualizovat tuto příponu** .

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Oznámení o selhání a nereagující na odezvu

Visual Studio vás upozorní, pokud při předchozí relaci došlo k chybě rozšíření. Pokud dojde k chybě sady Visual Studio, ukládá zásobník výjimek. Při příštím spuštění Visual Studio zjistí zásobníku, počínaje listu a funguje směrem k základní třídě. Pokud Visual Studio zjistí, že blok patří do modulu, který je součástí rozšíření nainstalované a povolené, zobrazuje oznámení o.

Visual Studio vás také upozorní, pokud se domnívá, že rozšíření způsobuje, že uživatelské rozhraní nereaguje.

Když tato oznámení jsou zobrazeny, můžete ignorovat oznámení nebo Absolvujte některou z následujících akcí:

::: moniker range="vs-2017"

- Zvolte **zakázat toto rozšíření**. Visual Studio zakáže rozšíření a poznáte, jestli je potřeba restartovat systém pro zakázání se projeví. Pokud chcete, můžete rozšíření znovu povolit v dialogovém okně **nástroje** > **rozšíření a aktualizace** .

::: moniker-end

::: moniker range=">=vs-2019"

- Zvolte **zakázat toto rozšíření**. Visual Studio zakáže rozšíření a poznáte, jestli je potřeba restartovat systém pro zakázání se projeví. Pokud chcete, můžete rozšíření znovu povolit v dialogovém okně **rozšíření** > **Spravovat rozšíření** .

::: moniker-end

- Zvolte **tuto zprávu již nezobrazovat**.

  - Pokud oznámení nastane při selhání v předchozí relaci, Visual Studio již nezobrazuje oznámení, když dojde k chybě spojené s tímto rozšířením. Visual Studio bude stále zobrazovat upozornění při zablokování můžou být spojené s touto příponou nebo zhroucení nebo zablokování, která můžou být spojené s další rozšíření.
  - Pokud oznámení nesouvisí s odezvou, integrované vývojové prostředí (IDE) již nezobrazuje oznámení, pokud je toto rozšíření přidruženo k nereagující odezvě. V aplikaci Visual Studio se stále zobrazují oznámení týkající se chyb pro toto rozšíření a oznámení o selhání a nereagujících na další rozšíření.

- Pokud chcete přejít na tuto stránku, klikněte na další **informace** .

- Zvolte **X** tlačítko na konci oznámení zavřete oznámení. Zobrazí se nové oznámení pro budoucí instance rozšíření jsou spojeny s zhroucení nebo zablokování uživatelského rozhraní.

> [!NOTE]
> Uživatelské rozhraní sekundový výpadek reakce nebo selhání oznámení znamená, že pouze jeden z tohoto rozšíření modulů v zásobníku byl při reagovat uživatelské rozhraní, nebo když došlo k selhání. To neznamená, že rozšíření samotné bylo nadměrné spotřeby. Je možné, že rozšíření s názvem kód, který je součástí sady Visual Studio, což je zase v uživatelském rozhraní nereaguje nebo dojde k chybě. Však oznámení může být stále užitečná, pokud rozšíření, která vedla k zablokování uživatelského rozhraní nebo při selhání není pro vás důležité. V takovém případě při zakázání rozšíření zabráněno zablokování uživatelského rozhraní nebo selhání v budoucnu, bez dopadu na vaši produktivitu.

## <a name="samples"></a>Ukázky

Při instalaci online ukázky je řešení uloženo na dvou místech:

- Pracovní kopie je uložena v umístění, které jste zadali při vytváření projektu.

- Samostatná hlavní kopie je uložena v počítači.

::: moniker range="vs-2017"

K provedení těchto úloh souvisejících s ukázkami můžete použít dialogové okno **nástroje** > **rozšíření a aktualizace** :

::: moniker-end

::: moniker range=">=vs-2019"

Pomocí dialogového okna **rozšíření** > **Spravovat rozšíření** můžete provádět tyto úlohy související s ukázkami:

::: moniker-end

- Zobrazit seznam hlavních kopií ukázek, které jste nainstalovali.

- Zakázat nebo odinstalovat hlavní kopii ukázky.

- Instalovat balíky ukázek, což jsou kolekce ukázek, které se týkají technologie nebo funkce.

- Nainstalujte jednotlivé online ukázky.

- Zobrazit upozornění na aktualizace při zveřejnění změny zdrojového kódu nainstalovaných ukázek.

- Aktualizujte hlavní kopii nainstalované ukázky, když je oznámení o aktualizaci.

## <a name="see-also"></a>Viz také:

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
