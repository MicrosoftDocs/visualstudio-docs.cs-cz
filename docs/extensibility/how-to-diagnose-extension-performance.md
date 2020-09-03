---
title: 'Postupy: Diagnostika výkonu rozšíření | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 542d8a6d6d90091aa7a800ef18f847fea6b1a81c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905902"
---
# <a name="measuring-extension-impact-in-startup"></a>Měření dopadu rozšíření při spuštění

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Zaměření na výkon rozšíření v aplikaci Visual Studio 2017

Na základě zpětné vazby od zákazníků se dokončila jedna z oblastí pro fokus pro vydání sady Visual Studio 2017 a výkon načtení řešení. Jako tým platformy sady Visual Studio jsme pracovali na zlepšení výkonu při spouštění a načítání řešení. Obecně platí, že naše měření naznačují nainstalovaná rozšíření můžou mít na těchto scénářích značný vliv.

Abychom uživatelům pomohli tento dopad pochopit, Přidali jsme do sady Visual Studio novou funkci, která upozorní uživatele na pomalá rozšíření. V některých případech Visual Studio detekuje nové rozšíření, které zpomaluje načtení nebo spuštění řešení. Při zjištění zpomalení se uživatelům v rozhraní IDE zobrazí oznámení, že jim ukáže nové dialogové okno spravovat výkon sady Visual Studio. K tomuto dialogovému oknu se taky dá vždycky získat pøístup z nabídky Help k procházení dříve zjištěných rozšíření.

![spravovat výkon sady Visual Studio](media/manage-performance.png)

Tento dokument má za cíl pomáhat vývojářům rozšíření tím, že popisuje, jak se vypočítává dopad na rozšíření. Tento dokument také popisuje, jak lze analyzovat dopad na rozšíření v místním prostředí. Místní analýza dopadu na rozšíření určí, jestli se může rozšíření zobrazit jako rozšíření s vlivem na výkon.

> [!NOTE]
> Tento dokument se zaměřuje na dopad rozšíření při spuštění a zatížení řešení. Rozšíření mají také vliv na výkon sady Visual Studio, když způsobí, že uživatelské rozhraní přestane reagovat. Další informace o tomto tématu naleznete v tématu [How to: diagnostice zpoždění uživatelského rozhraní způsobeného rozšířeními](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Jak můžou rozšíření ovlivnit spuštění

Jedním z nejběžnějších způsobů rozšíření pro ovlivnění výkonu při spuštění je výběr automatického načítání do jednoho ze známých kontextů uživatelského rozhraní pro spuštění, jako je NoSolutionExists nebo ShellInitialized. Tyto kontexty uživatelského rozhraní se aktivují během spouštění. Všechny balíčky, které obsahují `ProvideAutoLoad` atribut v definici s těmito kontexty, budou načteny a inicializovány v daném čase.

Při měření dopadu rozšíření se primárně zaměřujeme na čas strávený těmito rozšířeními, která se v kontextech vyberou k automatickému načtení. Měřené časy by zahrnovaly, ale nemusely být omezeny na:

* Načítání sestavení rozšíření pro synchronní balíčky
* Doba strávená konstruktorem třídy balíčku pro synchronní balíčky
* Doba strávená metodou inicializace balíčku (nebo SetSite) pro synchronní balíčky
* V případě asynchronních balíčků jsou výše uvedené operace spouštěny ve vlákně na pozadí.  V takovém případě jsou operace vyloučeny z monitorování.
* Čas strávený při jakékoli asynchronní práci naplánované během inicializace balíčku pro spuštění v hlavním vlákně
* Čas strávený v obslužných rutinách událostí, konkrétně aktivace kontextu inicializace prostředí nebo změna stavu prostředí zombie
* Počínaje verzí Visual Studio 2017 Update 3 začneme i čas monitorování strávený při nečinném volání před inicializací prostředí shell. Dlouhé operace v obslužných rutinách nečinných také způsobují nereagující IDE a přispívají ke zjištěnému času spuštění uživatelem.

Přidali jsme spoustu funkcí počínaje verzí Visual Studio 2015. Tyto funkce vám pomůžou při odebírání potřebných balíčků k automatickému načtení. Tyto funkce také odloží nutnost načíst balíčky do více konkrétních případů. Mezi tyto případy patří příklady, kdy by se uživatelé lépe používali rozšíření nebo snížili dopad rozšíření při automatickém načítání.

Další podrobnosti o těchto funkcích najdete v následujících dokumentech:

[Kontexty uživatelského rozhraní založené na pravidlech](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): bohatší modul založený na pravidlech, který je založený na KONTEXTECH uživatelského rozhraní, umožňuje vytvářet vlastní kontexty založené na typech projektů, charakterech a atributech. Vlastní kontexty lze použít k načtení balíčku během konkrétnějších scénářů. Tyto konkrétní scénáře zahrnují přítomnost projektu se specifickou funkcí místo spuštění. Vlastní [kontexty také umožňují, aby viditelnost příkazů bylo vázané na vlastní kontext](visibilityconstraints-element.md) založený na komponentách projektu nebo jiných dostupných podmínek. Tato funkce eliminuje nutnost načtení balíčku pro registraci obslužné rutiny dotazu na stav příkazu.

[Podpora asynchronních balíčků](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Nová základní třída AsyncPackage v aplikaci visual Studio 2015 umožňuje asynchronní načtení balíčků sady Visual Studio na pozadí, pokud je zatížení balíčku vyžádáno atributem auto Load nebo asynchronním dotazem na službu. Toto načítání na pozadí umožňuje, aby rozhraní IDE mohlo reagovat. Integrované vývojové prostředí (IDE) reaguje i v době, kdy se rozšíření inicializuje na pozadí a kritické scénáře, jako je například spuštění a načtení řešení, by ovlivnilo.

[Asynchronní služby](how-to-provide-an-asynchronous-visual-studio-service.md): Díky podpoře asynchronních balíčků jsme také přidali podporu pro asynchronní dotazování na služby a mohli registrovat asynchronní služby. Důležitější je, že pracujeme na převedení základních služeb sady Visual Studio na podporu asynchronního dotazu tak, aby většina práce v asynchronním dotazu probíhat v vláknech na pozadí. SComponentModel (hostitel MEF sady Visual Studio) je jednou z hlavních služeb, které nyní podporují asynchronní dotaz, aby rozšíření podporovala kompletní asynchronní načítání.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Omezení dopadu automaticky načtených rozšíření

Pokud je nutné při spuštění balíčku i nadále automaticky načíst balíček, je důležité minimalizovat práci prováděnou při inicializaci balíčku. Minimalizace práce při inicializaci balíčku snižuje pravděpodobnost, že by rozšíření ovlivnilo spuštění.

Některé příklady, které by mohly způsobit nákladný inicializaci balíčku:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Použití synchronního zatížení balíčku namísto asynchronního načtení balíčku

Vzhledem k tomu, že synchronní balíčky jsou ve výchozím nastavení načítány do hlavního vlákna, doporučujeme, aby vlastníci rozšíření, které mají automaticky načtené balíčky, používali základní třídu balíčku, a to jak je uvedeno výše. Změna automaticky načteného balíčku pro podporu asynchronního načítání také usnadňuje řešení dalších problémů uvedených níže.

### <a name="synchronous-filenetwork-io-requests"></a>Synchronní požadavky na vstupně-výstupní operace souborů/sítě

V ideálním případě by se měl v hlavním vlákně vyhnout Jakýkoli synchronní soubor nebo požadavek na vstupně-výstupní operace v síti. Jejich dopad bude záviset na stavu počítače a může v některých případech zablokovat dlouhou dobu.

Použití asynchronního načítání balíčků a asynchronních vstupně-výstupních rozhraní API by mělo mít jistotu, že inicializace balíčku v takových případech neblokuje hlavní vlákno. Uživatelé mohou i nadále pracovat se sadou Visual Studio i v případě, že vstupně-výstupní požadavky probíhají na pozadí.

### <a name="early-initialization-of-services-components"></a>Časná inicializace služeb, součástí

Jedním z běžných vzorů při inicializaci balíčku je inicializace služeb, které používá nebo poskytuje tento balíček v balíčku `constructor` nebo `initialize` metodě. I když to zajišťuje, aby byly služby připravené k použití, může také přidat zbytečné náklady na načtení balíčku, pokud se tyto služby nepoužijí okamžitě. Místo toho by se takové služby měly inicializovat na vyžádání, aby se minimalizovala práce při inicializaci balíčku.

U globálních služeb poskytovaných balíčkem můžete použít `AddService` metody, které přijímají funkci, aby laxně vytvářená inicializaci služby pouze v případě, že je požaduje komponenta. Pro služby, které jsou používány v rámci balíčku, můžete použít opožděné \<T> nebo AsyncLazy \<T> , abyste se ujistili, že se služby inicializují nebo dotazují při prvním použití.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Měření dopadu automaticky načtených rozšíření pomocí protokolu aktivit

Počínaje verzí Visual Studio 2017 Update 3 znamená, že protokol aktivit sady Visual Studio nyní obsahuje položky pro dopad na výkon balíčků během spouštění a načítání řešení. Chcete-li zobrazit tato měření, je nutné otevřít Visual Studio s přepínačem/log a otevřít soubor *ActivityLog.xml* .

V protokolu aktivit budou položky pod položkou "spravovat výkon sady Visual Studio" a budou vypadat jako v následujícím příkladu:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Tento příklad ukazuje, že balíček s identifikátorem GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" strávil 2008 MS při spuštění sady Visual Studio. Všimněte si, že sada Visual Studio považuje náklady na nejvyšší úroveň jako primární číslo při výpočtu dopadu balíčku, který by byl uživatelům úspor zobrazený, když zakazují rozšíření pro daný balíček.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Měření dopadu automaticky načtených rozšíření pomocí PerfView

I když analýza kódu může pomoci identifikovat cesty kódu, které mohou zpomalit inicializaci balíčku, můžete také využít trasování pomocí aplikací, jako je PerfView, pro pochopení dopadu zátěže balíčku při spuštění sady Visual Studio.

PerfView je nástroj pro trasování v rámci systému. Tento nástroj vám pomůže pochopit cesty k provozu v aplikaci z důvodu využití procesoru nebo blokování systémových volání. Níže je uveden rychlý příklad analýzy ukázkového rozšíření pomocí PerfView, který je k dispozici na [webu Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Příklad kódu:**

Tento příklad vychází z níže uvedeného ukázkového kódu, který je navržený tak, aby zobrazoval případ některé běžné prodlevy:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Záznam trasování s PerfView:**

Po nastavení prostředí sady Visual Studio s nainstalovaným rozšířením můžete zaznamenat trasování po spuštění otevřením PerfView a otevřením dialogového okna **shromáždit** v nabídce **shromáždit** .

![Nabídka Collect PerfView](media/perfview-collect-menu.png)

Výchozí možnosti budou poskytovat zásobníky volání pro spotřebu procesoru, ale vzhledem k tomu, že se zajímá i čas blokování, byste měli také povolit zásobníky **času vlákna** . Až budou nastavení připravena, můžete kliknout na **Start Collection (spustit shromažďování** ) a po zahájení nahrávání otevřít Visual Studio.

Než zastavíte shromažďování, chcete se ujistit, že je sada Visual Studio plně inicializovaná, hlavní okno je zcela viditelné a pokud má vaše rozšíření nějaké části uživatelského rozhraní, které se automaticky zobrazí, jsou také viditelné. Po úplném načtení sady Visual Studio a inicializaci rozšíření můžete zastavit nahrávání a analyzovat trasování.

**Analýza trasování pomocí PerfView:**

Po dokončení nahrávání PerfView automaticky otevře možnosti trasování a rozbalí se.

Pro účely tohoto příkladu se primárně zajímáme o zobrazení **zásobníků času vlákna** , která můžete najít v části **Rozšířená skupina**. Toto zobrazení zobrazí celkový čas strávený na vlákně metodou, včetně času procesoru i času zablokování, jako je například vstupně-výstupní operace disku nebo čekání na popisovače.

 ![zásobníky času vlákna](media/perfview-thread-time-stacks.png)

 Během otevírání zobrazení **zásobníků času vlákna** byste měli zvolit proces **devenv** pro spuštění analýzy.

PerfView obsahuje podrobné pokyny pro čtení zásobníků času vlákna v rámci vlastní nabídky Help pro podrobnější analýzu. Pro účely tohoto příkladu chceme toto zobrazení dál filtrovat tím, že zahrnete zásobníky s názvem modulu balíčků a spouštěcím vláknem.

1. Pokud chcete odebrat jakékoli seskupení přidané ve výchozím nastavení, nastavte **GroupPats** na prázdný text.
2. Nastavte **IncPats** tak, aby zahrnoval část názvu sestavení a spouštěcího vlákna společně s existujícím filtrem procesu. V takovém případě by měl být **devenv; Spouštěcí vlákno; MakeVsSlowExtension**.

Nyní zobrazení zobrazí pouze náklady, které jsou spojeny se sestaveními souvisejícími s rozšířením. V tomto zobrazení se pokaždé, když se ve sloupci **Inc (včetně nákladů)** v spouštěcím vlákně nachází v souvislosti s naším filtrovaným rozšířením, a bude mít vliv na spuštění.

Pro příklad výše některých zajímavých zásobníků volání by byl:

1. V/v použití `System.IO` třídy: i když náklady na tyto rámce nemusí být v trasování příliš nákladné, jsou potenciální příčinou problému, protože se rychlost vstupně-výstupních operací souborů liší od počítače až po počítač.

   ![systémové vstupně-výstupní rámce](media/perfview-system-io-frames.png)

2. Blokování volání čekajících na jinou asynchronní práci: v tomto případě by celková doba představovala dobu, po kterou je hlavní vlákno blokováno při dokončení asynchronní práce.

   ![blokování rámců volání](media/perfview-blocking-call-frames.png)

Jedno z dalších zobrazení v trasování, které bude užitečné k určení dopadu, budou **načtena jako zásobníky imagí**. Můžete použít stejné filtry jako použité v zobrazení **zásobníků času vlákna** a zjistit všechna sestavení načtená z důvodu kódu spuštěného automaticky načteným balíčkem.

Je důležité minimalizovat počet načtených sestavení v rámci rutiny inicializace balíčku, protože každé další sestavení bude zahrnovat další vstupně-výstupní operace disku, což může zpomalit spouštění významně na pomalejších počítačích.

## <a name="summary"></a>Shrnutí

Po spuštění sady Visual Studio byla jednou z oblastí, na které průběžně získáváme zpětnou vazbu. Náš cíl uvedený výše je pro všechny uživatele, kteří mají konzistentní prostředí pro spouštění bez ohledu na to, které součásti a rozšíření nainstalovaly. Rádi bychom mohli spolupracovat s vlastníky rozšíření, abychom jim pomohli dosáhnout tohoto cíle. Výše uvedené pokyny by měly být užitečné při porozumění vlivu rozšíření na spuštění a buď k tomu, aby se zabránilo nutnosti automatického načítání nebo načítání asynchronně, aby se minimalizoval dopad na produktivitu uživatelů.
