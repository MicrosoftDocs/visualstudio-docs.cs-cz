---
title: R pracovní prostory
description: Jak řídit, kde r kód běží pomocí pracovních prostorů v sadě Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 97ce4f226c39a20ad41c5977f800aa178450c69c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302649"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Řízení, kde je spuštěn kód R s pracovními prostory

Pracovní prostor v nástroji R pro visual studio (RTVS) umožňuje nakonfigurovat, kde se spustí relace R, což se může stát v místních i vzdálených počítačích. Cílem je umožnit práci na srovnatelnéuživatelské prostředí, což vám dává možnost využít potenciálně výkonnější cloudové počítače.

Chcete-li otevřít okno **Pracovní prostory,** použijte příkaz **R Tools** > **pro pracovní prostory systému** **Windows** > nebo stiskněte **kombinaci kláves Ctrl**+**9**.

![Okno pracovních prostorů v nástrojích R pro Visual Studio (VS2017)](media/workspaces-window.png)

V tomto okně zelená značka zaškrtnutí označuje aktivní pracovní prostor, ke kterému je rtvs vázána. Výběrem modré šipky nastavíte aktivní pracovní prostor. Ikona nastavení (ozubeného kola) napravo od každého pracovního prostoru umožňuje změnit její název, umístění a argumenty příkazového řádku. Červené X odebere ručně přidanou pracovní plochu.

## <a name="save-and-reset-a-workspace"></a>Uložení a obnovení pracovního prostoru

Ve výchozím nastavení rtvs neukládá stav pracovního prostoru při zavření a znovu otevření projektu. Toto chování však můžete změnit pomocí [možností pracovního prostoru](options-for-r-tools-in-visual-studio.md#workspace).

Příkaz**Obnovení** **relace** >  **nástrojů** > R a tlačítko obnovit panel nástrojů v interaktivním okně také kdykoli obnoví stav pracovního prostoru. Pomocí vzdálených pracovních prostorů resetodstraní profil uživatele vytvořený při prvním připojení ke vzdálenému serveru, což účinně odstraní všechny soubory, které se tam nahromadily.

## <a name="local-workspaces"></a>Místní pracovní prostory

V seznamu Místní pracovní prostory se zobrazí všechny překladače Jazyka R, které jste nainstalovali do počítače.

Při spuštění sady Visual Studio se pokusí automaticky rozpoznat všechny verze jazyka R, které jste nainstalovali, a to tak, že se podíváte na klíč registru **HKEY_LOCAL_MACHINE\Software\R-Core.\\ ** Vzhledem k tomu, že tato kontrola se provádí pouze při spuštění, je třeba restartovat visual studio, pokud nainstalujete nový překladač R.

RTVS nemusí detekovat překladač R, který je nainstalován nestandardním způsobem (například při jednoduchém kopírování souborů do složky namísto spuštění instalačního programu). V takovém případě ručně vytvořte nový místní pracovní prostor R následujícím způsobem:

1. V okně Pracovní prostory vyberte tlačítko **Přidat.**
1. Zadejte název nového pracovního prostoru.
1. Zadejte cestu ke kořenové složce R, která obsahuje složku *přihrádky* s interpretem, spolu s libovolnými volitelnými argumenty příkazového řádku, které mají být předávány interpretovi při spuštění RTVS.
1. Po dokončení vyberte **Uložit**.

![Přidání nového pracovního prostoru](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Vzdálené pracovní prostory

Vzdálené pracovní prostory umožňují připojit se k relaci R ve vzdáleném počítači. (Postup konfigurace počítače pro tento účel naleznete v tématu [Nastavení vzdálených pracovních prostorů.)](setting-up-remote-r-workspaces.md)

Visual Studio automaticky nerozpozná vzdálené pracovní prostory, takže je nutné je přidat ručně pomocí tlačítka **Přidat** v okně Pracovní prostory, jak je popsáno v předchozí části. V takovém případě zadejte identifikátor URI vzdáleného počítače, nikoli místní cestu.

> [!Important]
> Vzdálené pracovní prostory jsou identifikovány identifikátorem URI, který *musí používat protokol HTTPS* k zajištění ochrany osobních údajů a integrity komunikace se vzdáleným počítačem. Visual Studio se nemůže připojit ke vzdálenému počítači, který nepodporuje protokol HTTPS.

> [!Note]
> Vzdálené pracovní prostory jsou efektivně ve verzi preview. Pracujeme na lepší implementaci problému synchronizace souborů pro budoucí vydání a vítáme vaše nápady a zpětnou vazbu.

## <a name="remote-workspace-logon"></a>Vzdálené přihlášení k pracovnímu prostoru

Chcete-li se přihlásit do vzdáleného pracovního prostoru, je nutné použít uživatelské jméno a heslo.

### <a name="logon-to-windows-workspace"></a>Přihlášení do pracovního prostoru systému Windows

Pokud je vzdálený počítač nastaven tak, aby používal váš účet domény, můžete pomocí přihlášení k doméně přistupovat ke vzdálenému pracovnímu prostoru. Pokud tomu tak není, musíte `machine-name\username` použít formát pro přihlášení pomocí účtu počítače ve vzdáleném počítači.

### <a name="logon-to-linux-workspace"></a>Přihlášení k linuxovépracovní ploše

Chcete-li se přihlásit `<<unix>>\username` k účtu linux, použijte formát. Máte-li například účet s `ruser`názvem , měli byste zadat `<<unix>>\ruser`uživatelské jméno jako .

## <a name="switch-between-workspaces"></a>Přepínání mezi pracovními plochami

RTVS je vázána pouze na jeden pracovní prostor najednou. Vázaný pracovní prostor je označen malým zeleným zaškrtnutím v okně Pracovní prostory. Ve výchozím nastavení se RTVS váže na poslední otevřený místní pracovní prostor v předchozí relaci.

Chcete-li změnit aktivní pracovní prostor, vyberte modrou šipku vedle požadovaného pracovního prostoru. Tím se zobrazí výzva k uložení relace, ukončí aktuální pracovní prostor a přepne na nový.

> [!Tip]
> Chcete-li zakázat příkaz uložit, vyberte příkaz**Možnosti** **nástrojů** > R a `No` **před přepnutím možnosti pracovních prostorů** na nastavit dialogové okno Zobrazit potvrzení na . Viz [Možnosti pracovního prostoru](options-for-r-tools-in-visual-studio.md#workspace).

Pokud se pokusíte přepnout na místní pracovní prostor, který byl odinstalován, nebo na vzdálený pracovní prostor, který není k dispozici, rtvs nemusí být vázána na žádný pracovní prostor. V důsledku toho se může zobrazit chyba při zadání kódu v interaktivním okně nebo zkuste spustit kód jinak:

![Chyba, pokud není žádný pracovní prostor vázán na RTVS.](media/workspaces-disconnected-interactive-window.png)

Chcete-li tento problém opravit, přepněte do jiného pracovního prostoru v okně Pracovní prostory. Pokud nejsou k dispozici žádné pracovní prostory, je třeba nainstalovat překladač R. Můžete také zkusit restartovat Visual Studio, pokud jste nainstalovali interpreta při spuštění sady Visual Studio.

### <a name="switch-to-a-remote-workspace"></a>Přepnutí do vzdáleného pracovního prostoru

Služba RTVS vás při prvním připojení ke vzdálenému pracovnímu prostoru vyzve k zadání pověření a poté tato pověření uloží do mezipaměti (pomocí zabezpečené sušárny přihlašovacích údajů systému Windows) pro pozdější relace. Komunikace se vzdáleným serverem se pak provádí bezpečně přes HTTPS (což je vyžadováno).

V závislosti na konfiguraci serveru se může při připojování zobrazit upozornění na certifikát s názvem "Certifikát zabezpečení předložený vzdálenou službou R nám neumožňuje prokázat, že se skutečně připojujete k počítači (název)."

![Upozornění na certifikát podepsaný svým držitelem při připojování ke vzdálenému pracovnímu prostoru](media/workspaces-remote-self-signed-certificate-warning.png)

Certifikát je dokument předložený rtvs počítačem, ke kterému se pokoušíte připojit. Certifikát obsahuje pole, které identifikuje identifikátor URI tohoto počítače. Upozornění se zobrazí, když služba RTVS zjistí neshodu mezi identifikátorem URI v certifikátu a identifikátorem URI používaným pro připojení k počítači, což znamená, že mohlo dojít k ohrožení zabezpečení serveru.

Toto upozornění se však zobrazí také v případě, *že certifikát podepsaný svým držitelem* byl použit k povolení protokolu HTTPS ve vzdáleném počítači namísto použití protokolu od důvěryhodného zprostředkovatele. Další informace naleznete v [tématu Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Adresáře v místních a vzdálených počítačích

Ve výchozím nastavení je při spuštění nového překladače R v místním pracovním prostoru aktuální pracovní adresář *%userprofile%\Documents*. Adresář můžete kdykoli změnit pomocí příkazů**Pracovní ho adresáře** **nástroje** > R nebo klepnutím pravým tlačítkem myši na projekt v Průzkumníkovi řešení sady Visual Studio a výběrem příkazů, jako je **Nastavit pracovní adresář zde**.

Při prvním připojení ke vzdálenému počítači rtvs automaticky vytvoří profil uživatele na základě vašich pověření, který nastaví pracovní adresář do složky *Dokumenty* pod tímto profilem. Tato složka se používá pro všechny následující vzdálené relace, které používají stejná pověření.

V důsledku toho přesné umístění, kde je váš kód spustí se může lišit mezi místní a vzdálené pracovní prostory. V kódu pak vždy používejte relativní cesty k datovým souborům a tak, aby byl váš kód přenosný napříč pracovními prostory.

Všimněte si také, že se vzdálenými pracovními prostory zůstávají všechny soubory v pracovním adresáři na místě v rámci relací pro stejný profil uživatele. Jak již bylo uvedeno dříve, můžete tyto soubory odstranit pomocí příkazu**Obnovení** **relace** >  **nástrojů R** > (nebo tlačítka reset v interaktivním okně) při použití vzdáleného pracovního prostoru. Tento příkaz znovu odstraní profil uživatele ze serveru, který je znovu vytvořen při opětovném připojení.

## <a name="copy-project-files-to-remote-workspaces"></a>Kopírování souborů projektů do vzdálených pracovních prostorů

Při práci s projekty R v sadě Visual Studio má místní počítač vždy nejnovější soubory projektu, i když používáte vzdálený pracovní prostor. To znamená, že při otevření projektu v sadě Visual Studio (což obvykle znamená otevření řešení obsahujícího tento projekt), RTVS předpokládá, že obsah projektu jsou umístěny zcela v místním počítači. Vzdálený pracovní prostor je ve skutečnosti pouze dočasným hostitelem pro soubory projektu a veškerý výstup z kódu. To například znamená, že při `source` načítání souboru pomocí interaktivního okna musí být tento soubor již ve vzdáleném počítači v cestě, kterou zadáte, nebo musí být v aktuálním pracovním adresáři vzdáleného jazyka R (nastavený pomocí `setwd()` funkce).

Soubory jsou zkopírovány na vzdálený server následujícím způsobem:

- Chcete-li pracovat se soubory vzdáleně prostřednictvím interaktivního okna, musíte je nejprve zkopírovat ručně klepnutím pravým tlačítkem myši na tyto soubory (nebo projekt) v Průzkumníku řešení a výběrem **položky Source Selected**. U jednotlivých souborů jsou zkopírovány do pracovního adresáře na serveru. při kopírování projektu rtvs vytvoří složku pro projekt.

- Soubory můžete také kopírovat tak, že vyberete v Průzkumníku řešení a pak vyberete **vybrané zdrojové soubory**. Tato akce je načte do interaktivního okna a spustí je tam. Pokud je relace připojena ke vzdálenému počítači, soubory se tam nejprve zkopírují.

- Pokud je RTVS vázána na vzdálený pracovní prostor a stisknete **klávesu F5**, vyberte **možnost Ladění** > **spouštění ladění**nebo jinak spusťte spouštění kódu, RTVS ve výchozím nastavení automaticky zkopíruje soubor projektu do vzdáleného pracovního prostoru (viz níže, jak toto chování řídit).

- Všechny soubory, které již na serveru existují, jsou přepsány.

> [!Note]
> Vzhledem k tomu, že RTVS nemůže spolehlivě zachytit všechna volání funkce R, volání funkcí, jako `source()` jsou nebo `runApp()` (pro lesklé aplikace) v interaktivním *okně, nekopíruje* soubory do vzdáleného pracovního prostoru.

[Vlastnosti projektu](r-projects-in-visual-studio.md#project-properties) řídí, zda RTVS zkopíruje soubory při spuštění projektu a přesně které soubory jsou zkopírovány. Chcete-li otevřít tuto stránku, vyberte příkaz nabídky **Vlastnosti projektu** > **(název)** nebo klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a vyberte **vlastnosti**.

![Vlastnosti projektu spouštějí kartu s nastavením přenosu souborů](media/workspaces-remote-file-transfer-filter-settings.png)

Zde vlastnost **Přenést soubory při spuštění** určuje, zda rtvs zkopíruje soubory projektu automaticky. **Data k přenosu** hodnoty pak filtruje přesně, které soubory jsou přeneseny. Ve výchozím nastavení je pouze kopírování *. R*, *. Rmd*, *.sql*, *.md*a *.cpp* soubory. Toto chování zabraňuje nechtěnému kopírování velkých datových souborů na server při každém spuštění.

## <a name="copy-files-from-a-remote-workspace"></a>Kopírování souborů ze vzdáleného pracovního prostoru

Pokud skript R generuje soubory na serveru, můžete tyto soubory zkopírovat zpět klientovi `rtvs::fetch_file` pomocí funkce. Tato funkce přijímá minimálně vzdálenou cestu k souboru, který chcete zkopírovat do počítače, a volitelně cílovou cestu v počítači. Pokud cestu nezadáte, soubor se zkopíruje do složky *%userprofile%\Downloads.*
