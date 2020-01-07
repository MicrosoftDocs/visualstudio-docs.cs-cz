---
title: Najít – příkazové okno
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591525"
---
# <a name="findcommand-box"></a>pole Najít/příkaz

Můžete vyhledat text a spustit příkazy sady Visual Studio z pole **Najít/příkaz** . Pole **Najít/příkaz** je stále k dispozici jako ovládací prvek panelu nástrojů, ale ve výchozím nastavení se už nezobrazuje. Pole **Najít/příkaz** můžete zobrazit tak, že na panelu nástrojů **Standard** kliknete na **tlačítko Přidat nebo odebrat tlačítka** a pak zvolíte **Najít**.

Chcete-li spustit příkaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zaregistrujte ho pomocí znaku většího než ( **>** ).

Pole **Najít/příkaz** zachová poslední 20 zadaných položek a zobrazí je v rozevíracím seznamu. Seznam můžete procházet výběrem **kláves se šipkami**.

![Najít&#47;– příkazové okno](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Hledání textu

Ve výchozím nastavení, když zadáte text do pole **Najít/příkaz** a pak zvolíte klávesu **ENTER** , Visual Studio prohledá aktuální dokument nebo nástroj pomocí možností, které jsou zadány v dialogovém okně **najít v souborech** . Další informace najdete v tématu [hledání a nahrazování textu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Zadávání příkazů

Chcete-li použít pole **Najít/příkaz** k vystavení jednoho [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazu nebo aliasu místo hledání textu, představte příkaz symbolem větším než ( **>** ). Příklad:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternativně můžete také použít okno **příkaz** k zadání a spuštění jednoho nebo více příkazů. Některé příkazy nebo aliasy lze zadat a provádět sami; ostatní mají ve své syntaxi požadované argumenty. Seznam příkazů, které mají argumenty, naleznete v tématu [Visual Studio Commands](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Řídicí znaky

Znak blikajícího kurzoru ( **^** ) v příkazu znamená, že znak bezprostředně za ním je interpretován doslova, nikoli jako řídicí znak. To lze použít k vložení přímých uvozovek ( **"** ), mezer, počátečních lomítek, znakových přepínačů nebo jiných literálových znaků v parametru nebo hodnotě přepínače s výjimkou názvů přepínačů. Příklad:

```
>Edit.Find ^^t /regex
```

Stříška funguje stejně, ať už se jedná o vnitřní nebo vnější uvozovky. Pokud poslední znak na řádku stříška, je ignorován.

## <a name="see-also"></a>Viz také:

- [okno Příkaz](../ide/reference/command-window.md)
- [Hledání a nahrazování textu](../ide/finding-and-replacing-text.md)
