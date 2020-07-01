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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8266a7c70544d8a320658fcd8b9f5ad249162fe
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769578"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser – příkaz

Zobrazuje adresu URL, kterou zadáte v okně webového prohlížeče, a to buď v rámci integrovaného vývojového prostředí (IDE), nebo mimo rozhraní IDE.

## <a name="syntax"></a>Syntaxe

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
`URL`

Povinná hodnota. Adresa URL (Uniform Resource Locator) pro web

## <a name="switches"></a>Přepínače
/new

Nepovinný parametr. Určuje, že se stránka zobrazí v nové instanci webového prohlížeče.

/ext

Nepovinný parametr. Určuje, že se stránka zobrazí ve výchozím webovém prohlížeči mimo rozhraní IDE.

## <a name="remarks"></a>Poznámky
Alias pro příkaz **ShowWebBrowser –** je **Navigate** nebo **NAV**.

## <a name="example"></a>Příklad
Následující příklad zobrazuje domovskou stránku Microsoft Docs ve webovém prohlížeči mimo rozhraní IDE. Pokud je již otevřena instance webového prohlížeče, je použita. v opačném případě se spustí nová instance.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)