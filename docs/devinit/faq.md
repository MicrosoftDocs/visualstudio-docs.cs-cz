---
title: Nejčastější dotazy
description: Nejčastější dotazy k nástroji devinit
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: dd2da52a84d972e47b0e63905f0c4b6d4f7af9f3
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809318"
---
# <a name="frequently-asked-questions-for-devinit"></a>Nejčastější dotazy k devinit

## <a name="is-devinit-just-for-github-codespaces"></a>Je devinit jenom pro GitHub Codespaces?

Devinit je teď k dispozici jenom jako součást privátní beta verze GitHub Codespaces. V nadcházející verzi sady Visual Studio 2019 ale máme plány, které by zahrnovaly devinit.

## <a name="is-it-windows-only"></a>Je jenom Windows?
Ano, devinit se zaměřuje na vytváření vývojářských prostředí, která pracují pro vývojáře pomocí sady Visual Studio, což znamená Windows. Zvažujeme jiné platformy, ale mnoho z nich už má skvělé řešení, takže jsme chtěli začít se sadou Visual Studio a Windows.

## <a name="theres-no-tool-for-the-dependency-i-need"></a>Neexistuje žádný nástroj pro závislost, kterou potřebuji.

Je nám líto, ale Pokud jste součástí privátní beta verze GitHubu Codespaces, můžete se k nám vrátit prostřednictvím kanálu pro zpětnou vazbu pro soukromou verzi beta. Pokud nejste součástí privátní beta verze, pořád ještě neznáte váš názor na to, co potřebujete, a můžete zaslat problém do našich [dokumentů sady Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) s popiskem, `devinit` abyste si vyžádali podporu pro potřebný nástroj.

## <a name="something-went-wrong-how-do-i-debug"></a>Něco se pokazilo, jak se dá ladit?

Pokud devinit selže, první věc, kterou chcete vyzkoušet, je `--verbose / -v` příznak pro získání dalších informací. Pravděpodobnou příčinou problému je, že základní nástroj, na který devinit volá, narazí na problém. Podrobné informace protokolu by měly obsahovat informace o tom, kde se má podívat na další.

## <a name="why-not-just-a-script"></a>Proč ne pouze skript?

Nastavení prostředí prostřednictvím skriptu je časová stará technika a může fungovat skvěle. Pokud to pro vás funguje, použijte! devinit je další možnost pro vývojáře, pokud není nejlepší volbou pro skripty.

## <a name="why-not-a-container"></a>Proč není kontejner?

Kontejnery a Docker jsou skvělé nástroje pro nasazení prostředí prostřednictvím kódu. Existuje několik důvodů, proč kontejnery nemůžou být pro vás nejvhodnějším řešením:

1. Pokud chcete použít vývojové prostředí na ploše systému Windows.
1. Pokud již máte operační systém a chcete pouze vylepšit místo nasazení nového prostředí.

Z těchto důvodů devinit o přizpůsobení prostředí systému Windows, které máte v současnosti.

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>Další informace o nástrojích pro vytváření virtuálních počítačů (například Terraformu, balírna, Vagrant atd.)

K dispozici je spousta skvělých nástrojů pro vytváření imagí Windows a měli byste je používat! Nepovedlo se nám ale najít jeden, který splňuje všechny scénáře, na které jsme měli na mysli. Chceme, aby se devinit jako nástroj, který vývojářům umožňuje přizpůsobit své prostředí, a to bez ohledu na to, co je potřeba pro konkrétní úložiště a mít skvělou integraci se sadou Visual Studio, a ne jako nástroj k vytváření imagí virtuálních počítačů.

## <a name="what-about-winget"></a>Co je Winget?

devinit není správce balíčků, jako je Winget, a nechceme ho mít. Chceme, abyste mohli používat Winget s devinit a pracujeme na nástroji jenom pro to.

## <a name="how-are-restarts-handled"></a>Jak se restartuje zpracování?

Pokud cokoli, co devinit nainstaluje, vyžaduje restartování operačního systému, zobrazí se chybová zpráva v konzole. Musíte restartovat operační systém v době, která vám vyhovuje. Po restartování může být nutné znovu spustit devinit, pokud nebyly nainstalovány všechny závislosti.

## <a name="working-with-others"></a>Práce s ostatními

devinit je vše o tom, jak povolit používání celého ekosystému, který je tam nasazený, a nakonfigurovat závislosti, které vaše aplikace může mít. I když má devinit svůj názor na to, co poskytuje, devinit se většinou o tom, jak povolit spouštění jiných nástrojů z deklarativního souboru JSON.

Dnes je devinit jenom Začínáme a náš [seznam nástrojů](/devinit-tool-list.md) je jenom začátek.
