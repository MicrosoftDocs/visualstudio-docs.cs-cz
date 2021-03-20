---
title: Přehled Codespaces GitHubu (Preview)
description: Přečtěte si další informace o GitHub Codespaces se sadou Visual Studio a o tom, jak vám může usnadnit rozšiřování vývojového prostředí do cloudu.
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: a4bf2cf948b6df65ee0407c1cc736e8056820a54
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672784"
---
# <a name="what-is-github-codespaces-preview"></a>Co je GitHub Codespaces? (Preview)

> [!Important] 
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Doporučujeme, abyste se účastnili našeho [fóra komunity vývojářů](https://developercommunity.visualstudio.com/home) pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech. 

Vítá vás Codespaces! Jsme rádi, že jste tady.

GitHub Codespaces poskytuje cloudové vývojové prostředí pro jakékoli aktivity, ať už se jedná o dlouhodobý projekt, nebo krátkodobou úlohu, jako je například kontrola žádosti o přijetí změn.

Codespaces GitHubu navíc přináší spoustu výhod DevOps, jako je opakovatelnost a spolehlivost, &mdash; která se obvykle rezervovala pro produkční úlohy &mdash; do vývojového prostředí. Můžete také přizpůsobit GitHub Codespaces tak, aby byly k dispozici nástroje, procesy a konfigurace, které dáváte přednost a jsou tam závislé.

Tento dokument vám vysvětlí klíčové koncepty a zavádí Codespaces funkce. Pokud chcete začít, podívejte se na [použití sady Visual Studio s codespace](use-visual-studio-with-codespaces.md).

## <a name="concepts-and-features"></a>Koncepce a funkce

Funkce Codespaces GitHubu jsou postavené na několika základních konceptech. Tato část se zabývá těmito koncepty a poskytuje stručnou prohlídku funkcí.

### <a name="remote-development"></a>Vzdálený vývoj

Mnoho vývojářů dnes zkusí kód ve vzdálených nastaveních nebo virtuálních počítačích, které jsou nakonfigurované s konkrétními zásobníky pro vývoj a modul runtime. Jsou to proto, že jsou moc závažné, moc rušivé a v některých případech je prakticky nemožné nastavit tato vývojová prostředí místně. Také jednotliví uživatelé chtějí vyzkoušet nové technologie nebo nová rozhraní bez obav, že se jedná o počítače, které potřebují ke každodenní práci.

Při používání vzdálených prostředí a nástrojů umožňujících vzdálenou správu vývojářům pomáhá, často se jedná o režii správy počítačů. Konfigurace prostředí často komplikuje připojování a přepínání kontextu. GitHub Codespaces odstraňuje bariéry k rychlé registraci a přepínání kontextu tím, že umožňuje, aby existovalo mnoho prostředí současně. 

GitHub Codespaces poskytuje spravovaná řešení, která vám umožní soustředit se na produktivitu při instalaci. Codespaces GitHubu koncepčně a technicky rozšiřuje Visual Studio 2019 o vzdáleném vývoji. 

### <a name="about-codespaces"></a>O codespaces

Codespace je polovina back-endu Codespaces GitHubu. Je to místo, kde všechny výpočetní prostředky spojené s vývojem softwaru nastává: kompilování, ladění, obnovování atd. Vytvořením codespace se připraví všechno, co potřebujete k dokončení úkolu, přezkoumání žádosti o přijetí změn nebo spuštění nového projektu. Codespaces konfigurace modulu runtime, kompilátoru, ladicího programu, editoru, vlastních konfigurací dotfile a zdrojového kódu potřebného pro práci na projektu.

Codespaces hostované v cloudu poskytují následující výhody:

- Rychlé vytvoření a jednorázově. Vytvořte tolik, kolik potřebujete (omezení pro účty), a po dokončení je vyřadit.
- Spravují se, což snižuje celkovou údržbu za vás.
- Mají předvídatelné ceny a platíte jenom za to, co využijete. A k dispozici je integrované autopozastavit, které eliminují náklady na navýšení nákladů.
- Ukládají výpočetní prostředky. Když přesunete vývojovou úlohu do cloudu, uvolní se omezené prostředky na vašem osobním počítači.

## <a name="custom-configuration"></a>Vlastní konfigurace

Codespaces GitHubu je sestavená tak, aby vyhovovala nejširší škále projektů nebo úkolů. Můžete začít s funkcemi inteligentní konfigurace, které poskytují běžné výchozí hodnoty, nebo doladit codespace s [vlastní konfigurací](customize-codespaces.md).

Flexibilní konfigurace umožňuje vývojářům rychle se připojit k projektům s jedinečnou konfigurací a požadavky, které je obtížné použít na místním počítači. Kromě toho se reprodukovat codespaces eliminují problémy v mém počítači.

## <a name="personal-configuration"></a>Osobní konfigurace

Víme, že zachování osobních preferencí je důležité pro vývoj na codespace hostovaných v cloudu a dobře známých a přirozených. Codespaces vrstvy na GitHubu jsou individuální vlastní nastavení nad konfigurací codespace. Codespaces GitHubu podporuje osobní preference a konfiguraci pro editory a terminály.

Codespace se dá vytvořit s uživatelem specifickou kolekcí [vlastních dotfiles](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) (například `.bashrc` , `.gitconfig` atd.) a GitHub Codespaces automaticky synchronizuje vaši identitu, motivy a nastavení v Gitu, takže každý codespace, který jste vytvořili, vypadá a nehledá na možnosti prostředí konkrétního projektu.

## <a name="see-also"></a>Viz také

* [Jak používat Visual Studio s codespace](use-visual-studio-with-codespaces.md)
* [Přizpůsobení codespace](customize-codespaces.md)
* [Podporované funkce sady Visual Studio](supported-features-codespaces.md)
