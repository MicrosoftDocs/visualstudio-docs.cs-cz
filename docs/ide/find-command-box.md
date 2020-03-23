---
title: Pole Najít/příkaz
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591525"
---
# <a name="findcommand-box"></a>pole Najít/příkaz

Text můžete vyhledat a spustit příkazy sady Visual Studio z pole **Najít nebo příkaz.** Pole **Najít/příkaz** je stále k dispozici jako ovládací prvek panelu nástrojů, ale ve výchozím nastavení již není viditelné. Pole Najít **nebo Příkaz** můžete zobrazit tak, že na panelu nástrojů **Standardní** **vyberete Tlačítka pro přidání nebo odebrání** a pak zvolíte **Najít**.

Chcete-li [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spustit příkaz, předmluva**>** s větší než ( ) znaménko.

Pole **Najít/příkaz** zachová posledních 20 zadaných položek a zobrazí je v rozevíracím seznamu. Seznam můžete procházet výběrem **kláves se šipkami**.

![Příkazové pole Najít&#47;](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Hledání textu

Ve výchozím nastavení při zadávání textu v poli **Najít/Příkaz** a následném výběru klávesy **Enter** prohledá Visual Studio aktuální dokument nebo okno nástroje pomocí voleb, které jsou zadány v dialogovém okně **Najít v souborech.** Další informace naleznete v [tématu Hledání a nahrazování textu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Zadávání příkazů

Chcete-li použít pole **Najít/Příkaz** k vydání jednoho [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazu nebo aliasu místo hledání**>** textu, předkonejte příkaz se symbolem větší než ( ). Například:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Případně můžete také použít **okno Příkaz** pro zadávání a spouštění jednoho nebo více příkazů. Některé příkazy nebo aliasy mohou být zadány a provedeny samy; jiní mají požadované argumenty v jejich syntaxi. Seznam příkazů, které mají argumenty, naleznete v [tématu Visual Studio příkazy](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Řídicí znaky

Znak stříšky (**^**) v příkazu znamená, že znak bezprostředně za ním je interpretován doslovně, nikoli jako řídicí znak. To lze použít k vložení rovných uvozovek (**"**), mezery, úvodní lomítka, stříšky nebo jiné literály v parametru nebo přepnutí hodnoty, s výjimkou názvů přepínačů. Například:

```
>Edit.Find ^^t /regex
```

Stříška funguje stejně bez ohledu na to, zda je uvnitř nebo vně uvozovek. Pokud stříška je poslední znak na řádku, je ignorována.

## <a name="see-also"></a>Viz také

- [Příkazové okno](../ide/reference/command-window.md)
- [Hledání a nahrazení textu](../ide/finding-and-replacing-text.md)
