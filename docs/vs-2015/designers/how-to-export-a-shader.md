---
title: 'Postupy: Export shaderu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2225ce416fed4e97e998a50f70a0dc4c25908476
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664474"
---
# <a name="how-to-export-a-shader"></a>Postupy: Exportování shaderu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak pomocí Návrháře shaderu exportovat shader DGSL (Direct Graph shader Language), abyste ho mohli použít ve své aplikaci.

 Tento dokument ukazuje tuto aktivitu:

- Export shaderu

## <a name="exporting-a-shader"></a>Export shaderu
 Po vytvoření shaderu pomocí Návrháře shaderu a před jeho použitím v aplikaci je nutné ho exportovat ve formátu, který vaše grafické rozhraní API zná. Shader můžete vyexportovat různými způsoby pro splnění různých potřeb.

#### <a name="to-export-a-shader"></a>Export shaderu

1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otevřete soubor **grafu Visual shader (. DGSL)** .

     Pokud nemáte soubor **grafu vizuálních shaderů (. DGSL)** otevřený, vytvořte ho tak, jak je popsáno v tématu [How to: Create a Basic Color shader](../designers/how-to-create-a-basic-color-shader.md).

2. Na panelu nástrojů **Návrháře shaderů** vyberte možnost **Upřesnit**, **exportovat**, **exportovat jako**. Zobrazí se dialogové okno **exportovat shader** .

3. V rozevíracím seznamu **Uložit jako typ** vyberte formát, který chcete exportovat.

     Můžete zvolit následující formáty:

     **HLSL pixel shader (\*. HLSL)** Exportuje shader jako zdrojový kód HLSL (High Level shader Language). Tato možnost umožňuje změnit shader později i po jeho nasazení v aplikaci. To může zjednodušit ladění a opravování kódu na základě problémů koncových uživatelů, ale také usnadňuje uživateli upravit váš shader nežádoucím způsobem – například pro získání nerovné výhody v konkurenční hře. Může také prodloužit dobu načítání shaderu.

     **Kompilovaný pixel shader (\*. CSO)** Exportuje shader jako HLSLový kód. Tato možnost umožňuje změnit shader později i po jeho nasazení v aplikaci. To může zjednodušit ladění a opravování kódu na základě problémů koncových uživatelů, ale vzhledem k tomu, že shader je předem zkompilován, neposkytuje dodatečnou režii za běhu, když je shader načten aplikací. Dostatečně zkušení uživatelé mohou i nadále upravovat shader nevyžádanými způsoby, ale kompilování shaderu to dělá mnohem obtížnější.

     **Header (\*. h) C++**  Exportuje shader jako záhlaví ve stylu jazyka C, které definuje bajtové pole obsahující HLSL bajt. Tato možnost může být časově náročná na ladění a opravování kódu na základě problémů koncových uživatelů, protože aplikace musí být znovu zkompilována pro otestování opravy. Vzhledem k tomu, že tato možnost je obtížné, ale není nemožné, pro úpravu shaderu po jeho nasazení v aplikaci, prezentuje největší obtíže uživateli, který chce změnit shader nevyžádanými způsoby.

4. V poli se seznamem **název souboru** zadejte název exportovaného shaderu a pak klikněte na tlačítko **Uložit** .

## <a name="see-also"></a>Viz také
 [Postupy: Vytvoření základního](../designers/how-to-create-a-basic-color-shader.md) [Návrháře shaderů](../designers/shader-designer.md) pro barevný shader
