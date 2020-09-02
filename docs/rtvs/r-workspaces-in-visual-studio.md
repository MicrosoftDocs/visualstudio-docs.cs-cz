---
title: Pracovní prostory R
description: Jak ovládat, kde se kód R spouští pomocí pracovních prostorů v aplikaci Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 97ce4f226c39a20ad41c5977f800aa178450c69c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89314937"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Řízení, kde se kód R spouští s pracovními prostory

Pracovní prostor v Nástroje R pro Visual Studio (RTVS) umožňuje nakonfigurovat, kde se relace R spustí, ke kterému může dojít na místních i vzdálených počítačích. Cílem je umožnit vám pracovat s srovnatelným uživatelským prostředím, které vám umožní využít potenciálně výkonnější cloudové počítače.

Chcete-li otevřít okno **pracovní prostory** , použijte příkaz **nástroje R**  >  **Windows**  >  **pracovní prostory** systému Windows nebo stiskněte klávesu **CTRL** + **9**.

![Okno pracovních prostorů v Nástroje R pro Visual Studio (VS2017)](media/workspaces-window.png)

V tomto okně zelená značka zaškrtnutí označuje aktivní pracovní prostor, ke kterému je RTVS vázán. Výběrem modré šipky nastavíte aktivní pracovní prostor. Ikona nastavení (ozubeného kolečka) vpravo od jednotlivých pracovních prostorů umožňuje změnit její název, umístění a argumenty příkazového řádku. Červený symbol X odstraní ručně přidaný pracovní prostor.

## <a name="save-and-reset-a-workspace"></a>Uložení a obnovení pracovního prostoru

Ve výchozím nastavení RTVS při zavření a opětovném otevření projektu neukládá stav pracovního prostoru. Toto chování však můžete změnit prostřednictvím [možností pracovního prostoru](options-for-r-tools-in-visual-studio.md#workspace).

Příkaz pro obnovení relace **nástrojů R**  >  **Session**  >  **Reset** a tlačítko obnovit v interaktivním okně také obnoví stav pracovního prostoru. Se vzdálenými pracovními prostory při obnovení dojde k odstranění profilu uživatele vytvořeného při prvním připojení ke vzdálenému serveru, který efektivně odstraní všechny soubory, které se tam nashromáždily.

## <a name="local-workspaces"></a>Místní pracovní prostory

Seznam místních pracovních prostorů zobrazuje všechny překladače R, které máte nainstalované v počítači.

Po spuštění sady Visual Studio se pokusí automaticky zjistit všechny verze jazyka R, které jste nainstalovali, a to tak, že prohlížíte klíč registru **HKEY_LOCAL_MACHINE \software\r-Core \\ ** . Vzhledem k tomu, že se tato kontroly provádí pouze při spuštění, je nutné restartovat aplikaci Visual Studio, pokud instalujete nový překladač R.

RTVS nemusí detekovat Interpret R, který je nainstalovaný nestandardním způsobem (například při pouhém zkopírování souborů do složky namísto spuštění instalačního programu). V takovém případě ručně vytvořte nový místní pracovní prostor R následujícím způsobem:

1. V okně pracovní prostory vyberte tlačítko **Přidat** .
1. Zadejte název nového pracovního prostoru.
1. Zadejte cestu ke složce R root, což je ten, který obsahuje složku *bin* s překladačem, spolu s případnými volitelnými argumenty příkazového řádku, které se mají předat Překladači při spuštění RTVS.
1. Po dokončení vyberte **Uložit**.

![Přidává se nový pracovní prostor.](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Vzdálené pracovní prostory

Vzdálené pracovní prostory umožňují připojit se k relaci jazyka R na vzdáleném počítači. (Další informace o tom, jak nakonfigurovat počítač pro tento účel, najdete v tématu [Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md) .)

Visual Studio automaticky nezjišťuje vzdálené pracovní prostory, takže je musíte přidat ručně pomocí tlačítka **Přidat** v okně pracovní prostory, jak je popsáno v předchozí části. V takovém případě zadejte identifikátor URI vzdáleného počítače, nikoli místní cestu.

> [!Important]
> Vzdálené pracovní prostory jsou označeny identifikátorem URI, který *musí používat protokol HTTPS* k zajištění ochrany osobních údajů a integrity komunikace se vzdáleným počítačem. Visual Studio se nemůže připojit ke vzdálenému počítači, který nepodporuje protokol HTTPS.

> [!Note]
> Vzdálené pracovní prostory jsou efektivně ve verzi Preview. Pracujeme na lepší implementaci problému s synchronizací souborů pro budoucí vydání a Vítejte v nápadech a zpětnou vazbu.

## <a name="remote-workspace-logon"></a>Vzdálené přihlášení k pracovnímu prostoru

Pro přihlášení ke vzdálenému pracovnímu prostoru je nutné použít uživatelské jméno a heslo.

### <a name="logon-to-windows-workspace"></a>Přihlášení k pracovnímu prostoru systému Windows

Pokud je váš vzdálený počítač nastavený tak, aby používal váš doménový účet, můžete k přístupu ke vzdálenému pracovnímu prostoru použít přihlášení k doméně. Pokud tomu tak není, musíte použít `machine-name\username` formát pro přihlášení pomocí účtu počítače na vzdáleném počítači.

### <a name="logon-to-linux-workspace"></a>Přihlášení k pracovnímu prostoru systému Linux

Chcete-li se přihlásit k účtu Linux, použijte `<<unix>>\username` formát. Pokud máte například účet s názvem `ruser` , měli byste zadat uživatelské jméno jako `<<unix>>\ruser` .

## <a name="switch-between-workspaces"></a>Přepínání mezi pracovními prostory

RTVS je svázána pouze s jedním pracovním prostorem v jednom okamžiku. Vázaný pracovní prostor je označen malým zeleným zaškrtnutím v okně pracovní prostory. Ve výchozím nastavení RTVS váže k poslednímu otevřenému místnímu pracovnímu prostoru v předchozí relaci.

Chcete-li změnit aktivní pracovní prostor, vyberte modrou šipku vedle požadovaného pracovního prostoru. Zobrazí se výzva k uložení vaší relace, ukončí aktuální pracovní prostor a pak přepne na nový.

> [!Tip]
> Pokud chcete zakázat výzvu k uložení, vyberte příkaz Možnosti **nástrojů R**  >  **Options** a **před přepnutím pracovních prostorů do možnosti pracovní prostory nastavte možnost zobrazit potvrzovací dialog** `No` . Viz [Možnosti pracovního prostoru](options-for-r-tools-in-visual-studio.md#workspace).

Pokud se pokusíte přepnout na místní pracovní prostor, který se odinstaloval nebo ke vzdálenému pracovnímu prostoru, který není k dispozici, RTVS nemusí být vázán k žádnému pracovnímu prostoru. V důsledku toho se může zobrazit chyba při zadání kódu do interaktivního okna nebo pokusu o spuštění kódu v jiném.

![Chyba, pokud není k dispozici žádný pracovní prostor pro RTVS](media/workspaces-disconnected-interactive-window.png)

Pokud to chcete opravit, přepněte do jiného pracovního prostoru v okně pracovní prostory. Pokud nejsou k dispozici žádné pracovní prostory, je nutné nainstalovat překladač R. Můžete také zkusit restartovat aplikaci Visual Studio, pokud jste při spuštění sady Visual Studio nainstalovali překladač.

### <a name="switch-to-a-remote-workspace"></a>Přepnout na vzdálený pracovní prostor

RTVS vás vyzve k zadání přihlašovacích údajů při prvním připojení ke vzdálenému pracovnímu prostoru a pak tyto přihlašovací údaje uloží do mezipaměti (pomocí zabezpečeného zámku Windows Credential) pro pozdější relace. Komunikace se vzdáleným serverem se pak provede zabezpečeným protokolem HTTPS (což je povinné).

V závislosti na konfiguraci serveru se při připojování ke čtení může zobrazit upozornění certifikátu. "bezpečnostní certifikát prezentovaný vzdáleným R Services nám neumožňuje prokázat, že se k počítači skutečně připojujete (název)."

![Upozornění certifikátu podepsaného svým držitelem při připojení ke vzdálenému pracovnímu prostoru](media/workspaces-remote-self-signed-certificate-warning.png)

Certifikát je dokument prezentovaný RTVS počítači, ke kterému se pokoušíte připojit. Certifikát obsahuje pole, které identifikuje identifikátor URI daného počítače. Upozornění se zobrazí, pokud RTVS zjistí neshodu mezi identifikátorem URI v certifikátu a identifikátorem URI použitým pro připojení k počítači, což značí, že zabezpečení serveru mohlo být ohroženo.

Toto upozornění se ale zobrazí také v případě, že byl *certifikát podepsaný svým držitelem* použit k povolení protokolu HTTPS na vzdáleném počítači namísto použití některého z důvěryhodných zprostředkovatelů. Další informace najdete v tématu [Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Adresáře na místních a vzdálených počítačích

Ve výchozím nastavení se při spuštění nového překladače R v místním pracovním prostoru v aktuálním pracovním adresáři *%USERPROFILE%\Documents*. Kdykoli můžete kdykoli změnit adresář pomocí příkazů **nástroje R**pro  >  **pracovní adresář** nebo kliknutím pravým tlačítkem myši na projekt v sadě Visual Studio Průzkumník řešení a výběrem příkazů, jako je například **nastavit pracovní adresář**.

Když se poprvé připojíte ke vzdálenému počítači, RTVS automaticky vytvoří profil uživatele na základě vašich přihlašovacích údajů, který nastaví pracovní adresář na složku *dokumenty* v tomto profilu. Tato složka se používá pro všechny následné vzdálené relace, které používají stejné přihlašovací údaje.

V důsledku toho se přesné umístění, kde se váš kód spouští, může lišit mezi místními a vzdálenými pracovními prostory. Ve svém kódu vždy používejte relativní cesty k datovým souborům a tak, aby byl váš kód přenosný napříč pracovními prostory.

Všimněte si také, že se vzdálenými pracovními prostory zůstávají všechny soubory v pracovním adresáři v rámci relací pro stejný profil uživatele v platnosti. Jak už bylo uvedeno dříve, můžete tyto soubory odstranit pomocí příkazu jazyka **R**  >  **Session**  >  **reset** (nebo tlačítka obnovit v interaktivním okně) při použití vzdáleného pracovního prostoru. Tento příkaz odstraní profil uživatele ze serveru, který se znovu vytvoří při opětovném připojení.

## <a name="copy-project-files-to-remote-workspaces"></a>Kopírovat soubory projektu do vzdálených pracovních prostorů

Při práci s projekty R v aplikaci Visual Studio má místní počítač vždy nejnovější soubory projektu, i když používáte vzdálený pracovní prostor. To znamená, že když otevřete projekt v aplikaci Visual Studio (což obvykle znamená otevření řešení obsahujícího tento projekt), RTVS předpokládá, že obsah projektu se nachází zcela v místním počítači. Vzdálený pracovní prostor je v podstatě stejně jako dočasný hostitel pro soubory projektu a jakýkoli výstup z kódu. To znamená, že když nahráváte soubor pomocí `source` interaktivního okna, tento soubor musí být na vzdáleném počítači v cestě, kterou zadáte, nebo musí být v aktuálním pracovním adresáři vzdáleného překladače R (nastavte s `setwd()` funkcí).

Soubory se zkopírují na vzdálený server následujícím způsobem:

- Chcete-li pracovat se soubory vzdáleně pomocí interaktivního okna, je nutné je nejprve zkopírovat ručně kliknutím pravým tlačítkem myši na tyto soubory (nebo projekt) v Průzkumník řešení a vybráním **zdroje**. U jednotlivých souborů se zkopírují do pracovního adresáře na serveru. Při kopírování projektu RTVS vytvoří složku pro projekt.

- Soubory můžete také zkopírovat tak, že v Průzkumník řešení vyberete a pak vyberete **zdroj vybraných souborů**. Tato akce je načte do interaktivního okna a spustí se tam. Pokud je relace připojena ke vzdálenému počítači, soubory jsou nejprve zkopírovány.

- Když je RTVS vázán ke vzdálenému pracovnímu prostoru a stisknete klávesu **F5**, vyberte **ladění**  >  **Spustit ladění**nebo jinak spustit kód, RTVS ve výchozím nastavení automaticky zkopíruje soubor projektu do vzdáleného pracovního prostoru (viz níže pro řízení tohoto chování).

- Všechny soubory, které již existují na serveru, budou přepsány.

> [!Note]
> Vzhledem k tomu, že RTVS nemůže spolehlivě zachytit všechna volání funkcí R, volání funkcí jako `source()` nebo `runApp()` (pro lesklé aplikace) v *not* rámci interaktivního okna nekopíruje soubory do vzdáleného pracovního prostoru.

[Vlastnosti projektu](r-projects-in-visual-studio.md#project-properties) určují, zda RTVS kopíruje soubory při spuštění projektu a přesně které soubory jsou zkopírovány. Chcete-li otevřít tuto stránku, **Project**vyberte  >  příkaz nabídky**Vlastnosti projektu (název)** nebo klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a vyberte možnost **vlastnosti**.

![Karta pro spuštění vlastností projektu s nastavením přenosu souborů](media/workspaces-remote-file-transfer-filter-settings.png)

Zde je vlastnost **přenos souborů při spuštění** určuje, zda RTVS kopíruje soubory projektu automaticky. Hodnota **soubory k přenosu** pak filtruje přesně to, které soubory se přenášejí. Ve výchozím nastavení je určena pouze pro kopírování *. R*, *. Soubory RMD*, *. SQL*, *. MD*a *. cpp* . Toto chování zabraňuje neúmyslnému kopírování velkých datových souborů na server při každém spuštění.

## <a name="copy-files-from-a-remote-workspace"></a>Kopírování souborů ze vzdáleného pracovního prostoru

Pokud skript R generuje soubory na serveru, můžete tyto soubory zkopírovat zpátky do klienta pomocí `rtvs::fetch_file` funkce. Tato funkce přijímá minimálně vzdálenou cestu k souboru, který chcete zkopírovat do počítače, a volitelně také cílovou cestu v počítači. Pokud cestu nezadáte, zkopíruje se soubor do složky *%userprofile%\downloads* .
