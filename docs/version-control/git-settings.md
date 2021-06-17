---
title: Nastavení Gitu v Visual Studio
titleSuffix: ''
description: Zjistěte, Visual Studio vaše předvolby spravovat pomocí souborů .gitconfig a nastavení Gitu.
ms.date: 06/08/2021
ms.topic: conceptual
ms.author: prnadago
author: prnadago
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: f8dd9781833706a73b82a71236d42cc71c9fb9ec
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126637"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Nastavení a předvolby Gitu v Visual Studio

V Visual Studio můžete nakonfigurovat a zobrazit běžná nastavení a předvolby Gitu, jako je vaše jméno a e-mailová adresa, upřednostňované nástroje pro rozdíl a sloučení a další. Tato nastavení a předvolby můžete zobrazit  a nakonfigurovat v dialogovém okně Možnosti na stránce Globální nastavení **Gitu** (platí pro všechna vaše úložiště) nebo na stránce Nastavení úložiště **Git** (platí pro aktuální úložiště).

Můžete nakonfigurovat dva typy nastavení:

- [Nastavení Gitu](#git-settings) – Nastavení v této části odpovídají nastavením Gitu, která jsou uložená v konfiguračních souborech Gitu. Tato nastavení můžete zobrazit a upravit v Visual Studio, ale spravují je konfigurační soubory Gitu.
- [Visual Studio nastavení](#visual-studio-settings) – Nastavení v této části konfiguruje nastavení a předvolby související s Gitem, které spravuje Visual Studio.

## <a name="how-to-configure-settings"></a>Postup konfigurace nastavení

1. Pokud chcete nakonfigurovat nastavení Gitu Visual Studio, zvolte **Nastavení** z nabídky Git nejvyšší úrovně.

   :::image type="content" source="media/git-menu-settings.png" alt-text="Nabídka Git s výzvou k příkazu Settings (Nastavení).":::

2. Zvolte **Globální nastavení Gitu** **nebo Nastavení úložiště Git a** zobrazte a nakonfigurujte nastavení na globální úrovni nebo na úrovni úložiště.

   :::image type="content" source="media/source-control-settings.png" alt-text="Navigační podokno v dialogovém okně Možnosti s výzvou k nastavení Gitu":::

3. Můžete nakonfigurovat několik běžných nastavení Gitu, jak je popsáno v následujících částech tohoto článku. Po konfiguraci požadovaného nastavení vyberte **OK** a uložte aktualizovaná nastavení.

   :::image type="content" source="media/ok-button.png" alt-text="Oblast zobrazení dialogového okna Možnosti s výzvou k tlačítku OK.":::

## <a name="git-settings"></a>Nastavení Gitu

Můžete také nakonfigurovat a zkontrolovat některá z nejběžnějších nastavení konfigurace Gitu. Následující nastavení můžete zobrazit a upravit v Visual Studio, i když jsou spravovaná konfiguračními soubory Gitu.

- [Jméno a e-mail](#name-and-email)
- [Vyřazení vzdálených větví během načítání](#prune-remote-branches-during-fetch)
- [Přenahánět místní větev při nahánění](#rebase-local-branch-when-pulling)
- [Zprostředkovatel kryptografické sítě](#cryptographic-network-provider)
- [Pomocná nápověda k přihlašovacím údajům](#credential-helper)
- [Nástroje pro & rozdílových slučování](#diff--merge-tools)
- [Soubory Git](#git-files)
- [Vzdálená zařízení](#remotes)
- [Jiná nastavení](#other-settings)

>[!NOTE]
>Nastavení Gitu nakonfigurovaná Visual Studio  globálním nastavení odpovídají nastavením v konfiguračním souboru Gitu  specifickém pro uživatele a nastavení v Nastavení úložiště odpovídají nastavení v konfiguračním souboru specifickém pro úložiště. Další informace o konfiguraci Gitu najdete v kapitole Pro Git o přizpůsobení [Gitu,](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)v dokumentaci [ke git-config](https://git-scm.com/docs/git-config)a v referenčních informacích k [konfiguračním souborům pro Pro Git.](https://git-scm.com/docs/git-config#FILES) Pokud chcete nakonfigurovat nastavení Gitu, která nejsou Visual Studio, použijte příkaz k zápisu `git config` hodnoty do konfiguračních souborů: `git config [--local|--global|--system] section.key value` .

### <a name="name-and-email"></a>Jméno a e-mail

Jméno a e-mail, které poskytnete, se použije jako informace o potvrzení pro každé potvrzení. Toto nastavení je k dispozici v globálních oborech i v oborech úložiště a odpovídá user.name a `git config` [](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) [user.email](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail) nastavení.

1. V nabídce Git přejděte na **Nastavení.** Pokud chcete nastavit uživatelské jméno a e-mail na globální úrovni, přejděte na **Git Global Settings**; Pokud chcete nastavit uživatelské jméno a e-mail na úrovni úložiště, přejděte na **Nastavení úložiště Git.**

2. Zadejte uživatelské jméno a e-mail a pak uložte **kliknutím na OK.** 

   :::image type="content" source="media/user-email-setting.png" alt-text="Podokno Globální nastavení Gitu v dialogovém okně Možnosti s výzvou k uživatelskému jménu e-mailu.":::

### <a name="prune-remote-branches-during-fetch"></a>Vyřazení vzdálených větví během načítání

Vyřazování odebere větve vzdáleného sledování, které už ve vzdáleném zařízení neexistují, a pomáhá udržovat seznam větví čistý a aktuální. Toto nastavení je k dispozici v globálních oborech i v oborech úložiště a odpovídá nastavení `git config` [fetch.prune.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune)

Doporučujeme nastavit tuto možnost na **hodnotu True** na globální úrovni. Platná nastavení jsou následující:

- True (doporučeno)
- Ne
- Zrušit nastavení (výchozí)

1. V nabídce Git přejděte na **Nastavení.** Přejděte do **části Globální nastavení Gitu** a nakonfigurujte tuto možnost na globální úrovni. Přejděte do **Nastavení úložiště Git** a nakonfigurujte tuto možnost na úrovni úložiště.

2. Při **načítání nastavte pro prune remote branches (Vyřazení** vzdálených větví) **hodnotu True** (doporučeno). Výběrem **OK** soubor uložte.

:::image type="content" source="media/prune-setting.png" alt-text="Snímek obrazovky se zvýrazněnou možností Vyřazení vzdálených větví během načítání a vybranou možností True z rozevíracího seznamu":::    

### <a name="rebase-local-branch-when-pulling"></a>Přenahánět místní větev při nahánění

Změny provedené potvrzeními v aktuální větvi, které nejsou v upstreamové větvi, přehodí aktuální větev na upstreamovou větev a pak změny, které jste si odložili, odloží. Toto nastavení je k dispozici v globálních oborech i v oborech úložiště a odpovídá nastavení `git config` [pull.rebase.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) Platná nastavení jsou následující:

- True: Po načtení přenastavte aktuální větev nad upstreamovou větev.
- False: Sloučí aktuální větev do upstreamové větve.
- Zrušit nastavení (výchozí): Pokud není uvedeno v jiných konfiguračních souborech, sloučí aktuální větev do upstreamové větve.
- Interaktivní: Přehodnotte obsah v interaktivním režimu.
- Preserve (Zachovat): Přehodnoťte změny bez zploštění místně vytvořených potvrzení sloučení.

1. V nabídce Git přejděte na **Nastavení.** Přejděte do **části Globální nastavení Gitu** a nakonfigurujte tuto možnost na globální úrovni. Přejděte do **Nastavení úložiště Git** a nakonfigurujte tuto možnost na úrovni úložiště.

2. Při **přetahování nastavte Přebase local branch** (Přebase místní větev) a výběrem **OK** ji uložte.

    :::image type="content" source="media/rebase-setting.png" alt-text="Snímek obrazovky znázorňuje zvýrazněnou možnost &quot;Rebase local branch when pulling&quot; (Přebase místní větev při stažení) a vybranou hodnotu True z rozevíracího seznamu":::

V nástroji není možné nakonfigurovat možnost `pull.rebase` **Interactive** Visual Studio. Visual Studio nepodporuje interaktivní přenaklad.
Pokud chcete `pull.rebase` nakonfigurovat použití interaktivního režimu, použijte příkazový řádek.

### <a name="cryptographic-network-provider"></a>Zprostředkovatel kryptografické sítě

Zprostředkovatel kryptografické sítě je nastavení konfigurace Gitu v globálním oboru, které konfiguruje, který back-end TLS/SSL se má používat za běhu, a odpovídá nastavení `git config` [http.sslBackend.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) Hodnoty jsou následující:

- OpenSSL: Pro protokoly TLS a SSL použijte [OpenSSL.](https://www.openssl.org/)
- Zabezpečený kanál: Pro protokoly TLS a SSL použijte [schannel (Secure Channel).](/windows/win32/secauthn/secure-channel) Schannel je nativní řešení pro Windows, které přistupuje k windows Credential Store a umožňuje tak správu certifikátů na podnikové úrovni.
- Zrušit nastavení (výchozí): Pokud toto nastavení není nastaveno, je výchozím nastavením OpenSSL.

1. V nabídce Git přejděte na **Nastavení.** Toto nastavení **nakonfigurujete v** globálním nastavení Gitu.

2. Nastavte **zprostředkovatele kryptografické** sítě na požadovanou hodnotu a **výběrem OK** ji uložte.

   :::image type="content" source="media/network-provider-setting.png" alt-text="Snímek obrazovky se zvýrazněnou možností Zprostředkovatel kryptografické sítě s vybranou možností OpenSSL z rozevíracího seznamu":::

### <a name="credential-helper"></a>Pomocná nápověda k přihlašovacím údajům

Když Visual Studio vzdálenou operaci Gitu, vzdálený koncový bod může žádost odmítnout, protože vyžaduje zadání přihlašovacích údajů k žádosti. V tu chvíli Git vyvolá pomocný objekt přihlašovacích údajů, který vrátí přihlašovací údaje potřebné k provedení operace, a pak zkusí požadavek znovu. Použitý pomocník přihlašovacích údajů odpovídá nastavení `git config` [credential.helper.](https://git-scm.com/docs/gitcredentials) Je k dispozici v globálním oboru s následujícími hodnotami:

- GCM pro Windows: [Jako pomocná Správce přihlašovacích údajů git pro Windows.](https://github.com/microsoft/Git-Credential-Manager-for-Windows)
- GCM Core: [Jako Správce přihlašovacích údajů použijte Git Správce přihlašovacích údajů Core.](https://github.com/microsoft/Git-Credential-Manager-Core)
- Zrušit nastavení (výchozí): Pokud toto nastavení není nastavené, použije se pomocná služba přihlašovacích údajů nastavená v konfiguraci systému. Od verze Git pro Windows 2.29 je výchozím pomocníkem pro přihlašovací údaje GCM Core.

1. V nabídce Git přejděte na **Nastavení.** Toto nastavení **nakonfigurujete v** globálním nastavení Gitu.

2. Nastavte **pomocnou položku Přihlašovací** údaje na požadovanou hodnotu a výběrem **OK** ji uložte.

:::image type="content" source="media/credential-helper-setting.png" alt-text="Snímek obrazovky s nastavením pomocníka pro přihlašovací údaje v dialogovém okně Možnosti":::

### <a name="diff--merge-tools"></a>Nástroje pro & rozdílových slučování

Git zobrazí rozdíly a konflikty při slučování ve vašich upřednostňovaných nástrojích. Nastavení v této části odpovídá nastavení `git config` [diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) [a merge.tool.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) Výběrem možnosti Use Visual Studio (Použít nástroj pro sloučení nebo rozdíl) v části Git Global Settings (Globální nastavení **Gitu)** a Git Repository Settings (Nastavení úložiště **Git)** **můžete nakonfigurovat, aby** jako nástroj pro sloučení Visual Studio . Pokud chcete nakonfigurovat další nástroje diff a merge, použijte `git config` s [přepínačem diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) nebo [merge.tool.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool)

:::image type="content" source="media/tools-setting.png" alt-text="Snímek obrazovky, který znázorňuje oddíl pro nastavení výchozího nástroje Diff a nástroje Sloučit v dialogovém okně Možnosti":::

### <a name="git-files"></a>Soubory Git

K zobrazení a úpravě souborů [gitignore](https://git-scm.com/docs/gitignore) a [gitattributes](https://git-scm.com/docs/gitattributes) pro vaše úložiště můžete použít část Soubory **Gitu** v oboru Nastavení úložiště **Git.**

:::image type="content" source="media/git-files-setting.png" alt-text="Snímek obrazovky znázorňuje oddíl pro zobrazení a úpravu souborů Ignore a attributes v úložišti":::

### <a name="remotes"></a>Vzdálená zařízení

Pomocí podokna **Vzdálená úložiště** v části **Nastavení úložiště Git** můžete nakonfigurovat vzdálená úložiště pro vaše úložiště. Toto nastavení odpovídá vzdálenému [příkazu gitu](https://git-scm.com/docs/git-remote) a umožňuje přidat, upravit nebo odebrat vzdálená úložiště.

:::image type="content" source="media/remotes-settings.png" alt-text="Snímek obrazovky s podoknem Vzdálená úložiště Git v dialogovém okně Možnosti":::

### <a name="other-settings"></a>Jiná nastavení

Pokud chcete zobrazit všechna ostatní nastavení konfigurace Gitu, můžete otevřít a zobrazit samotné konfigurační soubory, nebo můžete spustit příkaz a `git config --list` zobrazit nastavení.

## <a name="visual-studio-settings"></a>Visual Studio nastavení

Následující nastavení spravují předvolby související s Gitem v Visual Studio a spravuje je Visual Studio místo konfiguračních souborů Gitu. Všechna nastavení v této části se konfiguruje na stránce **Globální nastavení Gitu.**

- [Výchozí umístění](#default-location)
- [Zavření otevřených řešení, která nejsou v Rámci Gitu, při otevírání úložiště](#close-open-solutions-not-under-git-when-opening-a-repository)
- [Povolení stahování imagí autorů ze zdrojů třetích stran](#enable-download-of-author-images-from-third-party-sources)
- [Potvrzení změn po sloučení ve výchozím nastavení](#commit-changes-after-merge-by-default)
- [Povolení nabízeného oznámení --force](#enable-push---force-with-lease)
- [Otevření složky v Průzkumník řešení při otevření úložiště Git](#open-folder-in-solution-explorer-when-opening-a-git-repository)
- [Automatické načtení řešení při otevření úložiště Git](#automatically-load-the-solution-when-opening-a-git-repository)
- [Automatické odhlášení větví poklikejte nebo stiskněte klávesu Enter.](#automatically-check-out-branches-with-double-click-or-the-enter-key)

### <a name="default-location"></a>Výchozí poloha

**Výchozí umístění** konfiguruje výchozí složku, ve které se klonuje úložiště.

:::image type="content" source="media/default-location-setting.png" alt-text="Snímek obrazovky s polem výchozího umístění v dialogovém okně Možnosti":::

### <a name="close-open-solutions-not-under-git-when-opening-a-repository"></a>Zavření otevřených řešení, která nejsou v Rámci Gitu, při otevírání úložiště

Ve výchozím nastavení Visual Studio jakékoli otevřené řešení nebo složku při přepnutí do jiného úložiště. Když to udělá, může také načíst řešení nebo složku nového úložiště podle toho, jestli se rozhodnete otevřít složku v Průzkumník řešení při otevření úložiště [Git a](#open-folder-in-solution-explorer-when-opening-a-git-repository) automaticky načíst řešení při otevření [úložiště Git.](#automatically-load-the-solution-when-opening-a-git-repository) Tím se udržuje konzistence mezi otevřeným kódem a otevřeným úložištěm. Pokud ale vaše řešení není ve stejném kořenovém adresáři složky jako vaše úložiště, možná budete chtít řešení nechat otevřené, když přepnete na jeho úložiště. Můžete to provést pomocí tohoto nastavení. Hodnoty jsou následující:

- Ano: Při otevření úložiště se aktuálně otevřené řešení vždy zavře.
- Ne: Při otevření úložiště Visual Studio zkontroluje, jestli se aktuální řešení nachází v Gitu. Pokud tomu tak není, zůstane řešení otevřené.
- Vždy se zeptat (výchozí): Pokud je toto nastavení nastavené, můžete si v dialogovém okně pro každý úložiště vybrat, jestli chcete aktuální řešení nechat otevřené nebo zavřít.

:::image type="content" source="media/close-sln-setting.png" alt-text="Snímek obrazovky s nastavením zavřít řešení v dialogovém okně Možnosti":::


### <a name="enable-download-of-author-images-from-third-party-sources"></a>Povolení stahování imagí autorů ze zdrojů třetích stran

Povolení stahování imagí autorů ze zdrojů třetích stran je Visual Studio specifické pro konkrétní nastavení v globálním oboru. Pokud je toto políčko zaškrtnuté, stáhnou se image autorů ze služby [Image Service Odtar,](https://en.gravatar.com/)pokud jsou k dispozici, a zobrazí se v zobrazení potvrzení a historie.

:::image type="content" source="media/download-image-setting.png" alt-text="Snímek obrazovky se zaškrtávacím políčkem pro povolení stahování imagí autorů ze zdroje třetí strany v dialogovém okně Možnosti ":::

>[!IMPORTANT]
>Aby nástroj mohl poskytovat obrázky autorů v zobrazeních Potvrzení a Historie, vytvoří hodnotu hash MD5 pro e-mailové adresy autora uložené v aktivním úložišti. Tato hodnota hash se pak odesílá do Společnosti, aby našla odpovídající hodnotu hash pro uživatele, kteří se ke službě zaregistrovali dříve. Pokud je nalezena shoda, obrázek uživatele se načte ze služby a zobrazí v Visual Studio. Uživatelé, kteří nenakonfigurovali službu, vrátí náhodně vygenerovaný obrázek. Upozorňujeme, že e-mailové adresy nejsou Visual Studio, ani se nikdy nesmějí se Společnostíatar nebo jinou třetí stranou.

### <a name="commit-changes-after-merge-by-default"></a>Potvrzení změn po sloučení ve výchozím nastavení

Když **je potvrzení změn po sloučení** ve výchozím nastavení povolené, Git při sloučení větve s aktuální větví automaticky vytvoří nové potvrzení.

:::image type="content" source="media/merge-commit-setting.png" alt-text="Snímek obrazovky se zaškrtávacím políčkem pro potvrzení změn po sloučení ve výchozím nastavení v dialogovém okně Možnosti":::

- Pokud je `git merge` tato možnost zaškrtnutá, Visual Studio se spustí s `--commit` parametrem .
- Pokud není tato možnost zaškrtnutá, příkazy Visual Studio `git merge` se spustí s `--no-commit --no-ff` možnostmi .

Další informace o těchto možnostech najdete v tématu [--commit a --no-commit](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) a [--no-ff.](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff)

### <a name="enable-push---force-with-lease"></a>Povolení nabízeného oznámení --force-with-lease

Pokud je toto nastavení povolené, můžete z `push --force-with-lease` Visual Studio. Ve výchozím **nastavení je možnost Enable push --force-with-lease** zakázaná.

:::image type="content" source="media/push-force-setting.png" alt-text="Snímek obrazovky se zaškrtávacím políčkem pro povolení vynucení nabízeného oznámení s zapůjčením v dialogovém okně Možnosti":::

Další informace najdete v tématu [push --force-with-lease.](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease)

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>Otevření složky v Průzkumník řešení při otevření úložiště Git
<!-- todo: write section -->
Když použijete Visual Studio k otevření nebo přepnutí do úložiště Git, načte Visual Studio obsah Gitu, abyste mohli zobrazit změny, potvrzení, větve a spravovat úložiště z integrovaného vývojového prostředí (IDE). Kromě toho Visual Studio také načte kód úložiště v Průzkumník řešení. Visual Studio prohledá složku úložiště pro řešení, CMakeLists.txt nebo jakékoli jiné soubory zobrazení, které rozpozná, a zobrazí je jako seznam v Průzkumník řešení. Odtud můžete vybrat řešení, které se má načíst, nebo složku pro zobrazení obsahu adresáře. Když toto políčko vypnete, Visual Studio neotevře složku úložiště v Průzkumník řešení. To vám v podstatě umožní otevřít Visual Studio jako správce úložiště Git. Toto nastavení je ve výchozím nastavení povoleno.

:::image type="content" source="media/open-folder-setting.png" alt-text="Snímek obrazovky se zaškrtávacím políčkem pro otevření složky při otevření úložiště Git v dialogovém okně Možnosti":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>Automatické načtení řešení při otevření úložiště Git

Toto nastavení platí jenom v případě, že je Průzkumník řešení otevřít složku v úložišti [Git](#open-folder-in-solution-explorer-when-opening-a-git-repository) zapnuté. Když otevřete úložiště Git v Visual Studio a následná kontrola složek zjistí, že ve vašem úložišti existuje pouze jedno řešení, Visual Studio toto řešení automaticky načte. Pokud toto nastavení vypnete, Průzkumník řešení v seznamu zobrazení zobrazí jediné řešení v úložišti. Řešení se ale nenačte. Ve výchozím nastavení je toto nastavení vypnuté.

:::image type="content" source="media/load-solution-setting.png" alt-text="Snímek obrazovky se zaškrtávacím políčkem pro automatické načtení řešení při otevření úložiště Git v dialogovém okně Možnosti":::

### <a name="automatically-check-out-branches-with-double-click-or-the-enter-key"></a>Automatické odhlášení větví poklikejte nebo stiskněte klávesu Enter.

Okno Úložiště Git obsahuje seznam větví zobrazených ve stromové struktuře. Jedním výběrem větve se přepne podokno historie potvrzení, aby se pro vybranou větev zobrazují potvrzení. Pokud chcete otevřít větev, kliknutím pravým tlačítkem otevřete místní nabídku a vyberte **Checkout (Pokladna).** Pokud toto nastavení zapnete, poklikáním nebo stisknutím klávesy Enter se větev otevře a zobrazí se její potvrzení. 
  
:::image type="content" source="media/checkout-branch-setting.png" alt-text="Snímek obrazovky se zaškrtávacím políčkem pro odhlášení větví poklikejte nebo klávesou Enter v dialogovém okně Možnosti":::


## <a name="see-also"></a>Viz také

> [!IMPORTANT]
> Pokud pro nás máte návrh, dejte nám vědět! Vážíme si příležitosti, abyste se mohli při rozhodování o návrhu zapojit prostřednictvím [**Developer Community**](https://aka.ms/vsgitsuggestions) Portalu.

- [Začínáme s Gitem a GitHubem v Visual Studio](/learn/modules/visual-studio-github-push/) kurzu k Microsoft Learn
- [Začínáme s Gitem ve Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) videu na YouTube
- [Vyšší produktivita díky Gitu v Visual Studio](https://devblogs.microsoft.com/visualstudio/enhanced-productivity-with-git-in-visual-studio/) blogovém příspěvku
- [Možnosti – dialogové okno](../ide/reference/options-dialog-box-visual-studio.md)
