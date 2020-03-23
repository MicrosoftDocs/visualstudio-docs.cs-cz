---
title: ShowWebBrowser – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747715"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser – příkaz

Zobrazí adresu URL zadanou v okně webového prohlížeče v integrovaném vývojovém prostředí (IDE) nebo externí prostředí IDE.

## <a name="syntax"></a>Syntaxe

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
`URL`

Povinná hodnota. URL (Jednotný lokátor zdrojů) pro web.

## <a name="switches"></a>Přepínače
/nový

Nepovinný parametr. Určuje, že se stránka zobrazí v nové instanci webového prohlížeče.

/ext

Nepovinný parametr. Určuje, že se stránka zobrazí ve výchozím webovém prohlížeči mimo prostředí IDE.

## <a name="remarks"></a>Poznámky
Alias příkazu **ShowWebBrowser** je **navigace** nebo **navigace**.

## <a name="example"></a>Příklad
Následující příklad zobrazuje domovskou stránku Microsoft Docs ve webovém prohlížeči mimo rozhraní IDE. Pokud je instance webového prohlížeče již otevřena, použije se; v opačném případě je spuštěna nová instance.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)