---
title: Vyhledání a instalace rozšíření
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594406"
---
# <a name="manage-extensions-for-visual-studio"></a>Správa rozšíření pro Visual Studio

Rozšíření jsou balíčky kódu, které běží v sadě Visual Studio a poskytují nové nebo vylepšené funkce. Rozšíření mohou být ovládací prvky, ukázky, šablony, nástroje nebo jiné součásti, které přidávají funkce do sady Visual Studio, například [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) nebo Visual [Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Informace o vytváření rozšíření sady Visual Studio naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md). Informace o použití rozšíření naleznete na stránce jednotlivých rozšíření na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Dialogové okno Rozšíření a aktualizace

Dialogové **okno Rozšíření a aktualizace** slouží k instalaci a správě rozšíření sady Visual Studio. Chcete-li otevřít dialogové okno **Rozšíření a aktualizace,** zvolte **Rozšíření** > **a aktualizace nástrojů**nebo do vyhledávacího pole Snadné **spuštění** zadejte **rozšíření.**

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Dialogové okno Spravovat rozšíření

Dialogové okno **Spravovat rozšíření** slouží k instalaci a správě rozšíření sady Visual Studio. Chcete-li otevřít dialogové okno **Spravovat rozšíření,** zvolte **Spravovat** > **rozšíření**. Nebo do vyhledávacího pole zadejte **Rozšíření** a zvolte **Spravovat rozšíření**.

::: moniker-end

![Okno rozšíření v sadě Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Podokno na levé straně kategorizuje rozšíření podle těch, které jsou nainstalovány, ty, které jsou k dispozici na Visual Studio Marketplace (**Online**) a ty, které mají k dispozici aktualizace. **Správce roamingových rozšíření** uchovává seznam všech rozšíření sady Visual Studio, která jste nainstalovali v libovolném počítači nebo instanci sady Visual Studio. Je navržen tak, aby vám umožní snadněji najít vaše oblíbená rozšíření.

## <a name="find-and-install-extensions"></a>Vyhledání a instalace rozšíření

::: moniker range="vs-2017"

Rozšíření můžete nainstalovat z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com) nebo z dialogového okna Rozšíření a aktualizace v sadě Visual Studio.

Instalace rozšíření z aplikace Visual Studio:

1. V **rozšíření nástroje** > **a aktualizace**, najít rozšíření, které chcete nainstalovat. Pokud znáte název nebo část názvu rozšíření, můžete hledat v okně **Hledat.**

2. Vyberte **Download** (Stáhnout).

   Rozšíření je naplánováno pro instalaci. Rozšíření bude nainstalováno po zavření všech instancí sady Visual Studio.

Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud nejsou **nainstalovány,** dialogové okno Rozšíření a aktualizace zobrazí seznam závislostí, které je nutné nainstalovat před instalací rozšíření.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Instalace bez použití dialogového okna Rozšíření a aktualizace

Rozšíření, která byla zabalena v souborech *.vsix,* mohou být k dispozici v jiných umístěních než na webu Visual Studio Marketplace. Dialogové okno**Rozšíření a aktualizace** **nástrojů** > tyto soubory nerozpozná, ale soubor *VSix* můžete nainstalovat poklepáním na soubor nebo výběrem souboru a stisknutím **klávesy Enter**. Poté postupujte podle pokynů. Po instalaci rozšíření můžete pomocí dialogového okna **Rozšíření a aktualizace** povolit, zakázat nebo odinstalovat.

> [!NOTE]
> - Visual Studio Marketplace obsahuje rozšíření VSIX i MSI. Dialogové okno Rozšíření a aktualizace nemůže povolit nebo zakázat rozšíření založená na MSI.
> - Pokud přípona založená na MSI obsahuje soubor *extension.vsixmanifest,* zobrazí se v dialogovém okně **Rozšíření a aktualizace.**

::: moniker-end

::: moniker range=">=vs-2019"

Rozšíření můžete nainstalovat z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com) nebo z dialogového okna Spravovat rozšíření v sadě Visual Studio.

Instalace rozšíření z aplikace Visual Studio:

1. V **rozšíření** > **spravovat rozšíření**, najít rozšíření, které chcete nainstalovat. (Pokud znáte název nebo část názvu rozšíření, můžete hledat v okně **Hledat.)**

2. Vyberte **Download** (Stáhnout).

   Rozšíření je naplánováno pro instalaci. Rozšíření bude nainstalováno po zavření všech instancí sady Visual Studio.

Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud nejsou **nainstalovány,** dialogové okno Spravovat rozšíření zobrazí seznam závislostí, které je nutné nainstalovat před instalací rozšíření.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Instalace bez použití dialogového okna Spravovat rozšíření

Rozšíření, která byla zabalena v souborech *.vsix,* mohou být k dispozici v jiných umístěních než na webu Visual Studio Marketplace. Dialogové **okno Správa** > **příponek** nemůže tyto soubory rozpoznat, ale soubor *VSix* můžete nainstalovat poklepáním na soubor nebo výběrem souboru a stisknutím **klávesy Enter**. Poté postupujte podle pokynů. Po instalaci rozšíření můžete pomocí dialogového okna **Spravovat rozšíření** povolit, zakázat nebo odinstalovat.

> [!NOTE]
> - Visual Studio Marketplace obsahuje rozšíření VSIX i MSI. Dialogové okno Spravovat rozšíření nemůže povolit nebo zakázat rozšíření založená na MSI.
> - Pokud přípona založená na MSI obsahuje soubor *extension.vsixmanifest,* zobrazí se v dialogovém okně **Spravovat rozšíření.**

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Odinstalace nebo zakázání rozšíření

Pokud chcete přestat používat rozšíření, lze jej zakázat nebo odinstalovat. Zakázáním rozšíření zůstane rozšíření nainstalováno, ale nedojde k jeho načtení. Vyhledejte rozšíření a klepněte na tlačítko **Odinstalovat** nebo **zakázat**. Restartujte Visual Studio, chcete-li uvolnit zakázané rozšíření.

> [!NOTE]
> Můžete zakázat Rozšíření VSIX, ale ne rozšíření, které byly nainstalovány pomocí MSI. Rozšíření nainstalovaná msi lze pouze odinstalovat.

## <a name="per-user-and-administrative-extensions"></a>Rozšíření pro jednotlivé uživatele a pro správu

Většina rozšíření je pro jednotlivé uživatele a jsou nainstalována ve složce *%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio verze\>\Extensions.\\ * Několik rozšíření jsou rozšíření pro správu a jsou nainstalována ve * \<složce instalace\\ sady Visual Studio>\Common7\IDE\Extensions.*

Chcete-li chránit systém před rozšířeními, která mohou obsahovat chyby nebo škodlivý kód, můžete omezit načtení rozšíření pro jednotlivé uživatele pouze v případě, že je sada Visual Studio spuštěna s normálními uživatelskými oprávněními. To znamená, že rozšíření pro jednotlivé uživatele jsou zakázány při spuštění sady Visual Studio se zvýšenými oprávněními.

Omezení při načítání rozšíření pro jednotlivé uživatele:

1. Otevřete stránku možností rozšíření (Rozšíření > **prostředí** > **Možnosti****nástroje** > **Options**).

2. Zrušte zaškrtnutí políčka **Načíst na uživatele, když běžíte jako správce.**

3. Restartujte sadu Visual Studio.

## <a name="automatic-extension-updates"></a>Automatické aktualizace rozšíření

Rozšíření se aktualizují automaticky, když je na webu Visual Studio Marketplace k dispozici nová verze. Nová verze rozšíření je zjištěna a nainstalována na pozadí. Při příštím spuštění sady Visual Studio bude spuštěna nová verze rozšíření.

Chcete-li zakázat automatické aktualizace, můžete tuto funkci zakázat pro všechna rozšíření nebo pouze pro konkrétní rozšíření.

::: moniker range="vs-2017"

- Chcete-li zakázat automatické aktualizace pro všechna rozšíření, zvolte odkaz **Změnit rozšíření a aktualizace** v dialogovém okně **Rozšíření** > **a aktualizace.** V dialogovém okně **Možnosti** odškrtnete **políčko Automaticky aktualizovat rozšíření**.

- Chcete-li zakázat automatické aktualizace pro konkrétní rozšíření, zaškrtněte políčko **Automaticky aktualizovat tuto** možnost rozšíření v podokně podrobností rozšíření na pravé straně dialogového okna Rozšíření a **aktualizace.**

::: moniker-end

::: moniker range=">=vs-2019"

- Chcete-li zakázat automatické aktualizace pro všechna rozšíření, zvolte odkaz **Změnit nastavení rozšíření** v dialogovém okně **Spravovat** > **rozšíření.** V dialogovém okně **Možnosti** odškrtnete **políčko Automaticky aktualizovat rozšíření**.

- Chcete-li zakázat automatické aktualizace pro konkrétní rozšíření, zaškrtněte políčko **Automaticky aktualizovat tuto** možnost rozšíření v podokně podrobností rozšíření na pravé straně dialogového okna Spravovat **rozšíření.**

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Oznámení o selhání a neodezvě

Visual Studio vás upozorní, pokud má podezření, že rozšíření došlo k chybě během předchozí relace. Když dojde k chybě Visual Studio, uloží zásobník výjimek. Při příštím spuštění sady Visual Studio zkontroluje zásobníku, počínaje list a pracuje směrem k základně. Pokud Visual Studio zjistí, že rámec patří do modulu, který je součástí nainstalované a povolené rozšíření, zobrazí oznámení.

Visual Studio také upozorní, pokud má podezření, rozšíření způsobuje uživatelskérozhraní neodpovídá.

Pokud se tato oznámení zobrazí, můžete oznámení ignorovat nebo provést jednu z následujících akcí:

::: moniker range="vs-2017"

- Zvolte **Zakázat toto rozšíření**. Visual Studio zakáže rozšíření a umožňuje vědět, zda je třeba restartovat systém pro zakázání se projeví. Rozšíření můžete znovu povolit v dialogovém okně**Rozšíření a aktualizace** **nástrojů,** > pokud chcete.

::: moniker-end

::: moniker range=">=vs-2019"

- Zvolte **Zakázat toto rozšíření**. Visual Studio zakáže rozšíření a umožňuje vědět, zda je třeba restartovat systém pro zakázání se projeví. Rozšíření můžete znovu povolit v **dialogovém** > okně**Spravovat rozšíření,** pokud chcete.

::: moniker-end

- Zvolte **Nikdy se tato zpráva znovu zobrazovat**.

  - Pokud oznámení týká selhání v předchozí relaci, Visual Studio již zobrazuje oznámení, když dojde k chybě přidružené k tomuto rozšíření. Visual Studio bude stále zobrazovat oznámení, když neodpovídá může být přidružena k tomuto rozšíření nebo pro selhání nebo nereagující, které mohou být přidruženy k jiným rozšířením.
  - Pokud oznámení se týká nereagující, integrované vývojové prostředí (IDE) již zobrazuje oznámení, pokud toto rozšíření je spojena s nereagující. Visual Studio se stále zobrazí oznámení související s selháním pro toto rozšíření a oznámení související s selháním a nereagující pro jiná rozšíření.

- **Chcete-li** přejít na tuto stránku, zvolte Další možnosti přechodu na tuto stránku.

- Zvolte tlačítko **X** na konci oznámení pro zavření oznámení. Nové oznámení se zobrazí pro budoucí instance rozšíření je spojena s selhání nebo nereagující uživatelskérozhraní.

> [!NOTE]
> Nereagující uživatelské rozhraní nebo oznámení o selhání znamená pouze to, že jeden z modulů rozšíření byl v zásobníku, když uživatelské rozhraní nereagovalo nebo když došlo k chybě. To nutně neznamená, že rozšíření sám byl viníkem. Je možné, že rozšíření s názvem kód, který je součástí sady Visual Studio, což mělo za následek nereagující uživatelské rozhraní nebo selhání. Oznámení však může být stále užitečné, pokud rozšíření, které vedlo k nereagorování nebo selhání uživatelského rozhraní, pro vás není důležité. V takovém případě zakázání rozšíření zabrání nereagující uživatelské rozhraní nebo selhání v budoucnu, aniž by to mělo vliv na vaši produktivitu.

## <a name="samples"></a>ukázky

Při instalaci online ukázky je řešení uloženo na dvou místech:

- Pracovní kopie je uložena v umístění, které jste zadali při vytváření projektu.

- Samostatná hlavní kopie je uložena v počítači.

::: moniker range="vs-2017"

K provádění těchto úloh **souvisejících** s ukázkami můžete použít dialogové okno Rozšíření a aktualizace **nástrojů:** >

::: moniker-end

::: moniker range=">=vs-2019"

K provádění těchto úloh souvisejících s **ukázkami** > můžete použít dialogové okno **Spravovat rozšíření:**

::: moniker-end

- Zobrazit seznam hlavních kopií ukázek, které jste nainstalovali.

- Zakázat nebo odinstalovat hlavní kopii ukázky.

- Instalovat balíky ukázek, což jsou kolekce ukázek, které se týkají technologie nebo funkce.

- Nainstalujte jednotlivé online ukázky.

- Zobrazit upozornění na aktualizace při zveřejnění změny zdrojového kódu nainstalovaných ukázek.

- Aktualizace hlavní kopie nainstalované ukázky při oznámení o aktualizaci.

## <a name="see-also"></a>Viz také

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
