---
title: Použití 3D prostředků ve hře nebo aplikaci
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3821262a456f9e3e764555fce5fc883b42d4ae9e
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768662"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Postupy: Používání 3D prostředků ve hře nebo aplikaci

Tento článek popisuje, jak můžete pomocí sady Visual Studio zpracovat 3D prostředky a zahrnout je do sestavení.

Po použití nástrojů v aplikaci Visual Studio k vytvoření 3D prostředků je dalším krokem jejich použití ve vaší aplikaci. Než je ale budete moct používat, musí se prostředky transformovat do formátu, který rozhraní DirectX dokáže pochopit. Pro snadnější transformaci prostředků poskytuje Visual Studio přizpůsobení sestavení pro každý druh assetu, který může vytvořit. Chcete-li zahrnout prostředky do sestavení, stačí provést konfiguraci projektu, aby používal vlastní nastavení sestavení, přidat prostředky do projektu a nakonfigurovat prostředky pro použití správného přizpůsobení sestavení. Potom můžete načíst prostředky do své aplikace a použít je vytvořením a vyplněním prostředků DirectX stejným způsobem jako v jakékoli jiné aplikaci DirectX.

## <a name="configure-your-project"></a>Konfigurace projektu

Před nasazením 3D prostředků v rámci sestavení je třeba, aby se v aplikaci Visual Studio dozvědělo o druzích prostředků, které chcete nasadit. Visual Studio už zná mnoho běžných typů souborů, ale vzhledem k tomu, že se 3D prostředky používají jenom některé druhy aplikací, Visual Studio nepředpokládá, že projekt sestaví tyto typy souborů. Můžete říct, že aplikace Visual Studio používá tyto druhy prostředků pomocí *přizpůsobení sestavení*– soubory, které aplikaci Visual Studio dávají informace o zpracování různých typů souborů vhodným způsobem – které jsou k dispozici pro každý typ assetu. Vzhledem k tomu, že tyto vlastní nastavení jsou aplikovány na jednotlivé projekty, stačí, když do projektu přidáte odpovídající vlastní nastavení.

### <a name="to-add-the-build-customizations-to-your-project"></a>Přidání vlastního nastavení sestavení do projektu

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **sestavit závislosti**  >  **sestavení**.

   Zobrazí se dialogové okno **Visual C++ soubory přizpůsobení sestavení** .

2. V části **Dostupné soubory vlastního nastavení sestavení**zaškrtněte políčka, která odpovídají typům assetů, které chcete použít v projektu, jak je popsáno v následující tabulce:

    |Typ assetu|Název vlastního nastavení sestavení|
    |----------------| - |
    |Textury a obrázky|**ImageContentTask (. targets;. props)**|
    |3D modely|**MeshContentTask (. targets;. props)**|
    |Shadery|**ShaderGraphContentTask (. targets;. props)**|

3. Klikněte na tlačítko **OK** .

## <a name="include-assets-in-your-build"></a>Zahrnutí prostředků do sestavení

Teď, když váš projekt ví o různých druzích 3D prostředků, které chcete použít, je dalším krokem sdělit, které soubory jsou 3D prostředky a jaké druhy prostředků jsou.

### <a name="to-add-an-asset-to-your-build"></a>Přidání assetu do sestavení

1. V **Průzkumník řešení**v projektu otevřete místní nabídku prostředku a zvolte možnost **vlastnosti**.

   Zobrazí se dialogové okno **Stránka vlastností** prostředku.

2. Ujistěte se, že vlastnosti **Konfigurace** a **platforma** jsou nastaveny na hodnoty, na které chcete změny použít.

3. V části **Vlastnosti konfigurace**zvolte **Obecné**a potom v mřížce vlastností v části **Obecné**nastavte vlastnost **typ položky** na příslušný typ položky kanálu obsahu. Například pro obrázek nebo soubor textury vyberte možnost **kanál obsahu obrázku**.

    > [!IMPORTANT]
    > Ve výchozím nastavení Visual Studio předpokládá, že mnoho druhů obrázkových souborů by mělo být zařazeno pomocí typu položky **obrázku** , který je součástí sady Visual Studio. Proto je třeba změnit vlastnost **typ položky** každého obrázku, který chcete zpracovat pomocí kanálu obsahu obrázku. Další typy zdrojových souborů kanálu obsahu pro 3D modely a grafiku vizuálního shaderu jsou ve výchozím nastavení správného **typu položky**.

4. Klikněte na tlačítko **OK** .

Níže jsou uvedené tři typy položek kanálu obsahu a jejich přidružené zdrojové a výstupní typy souborů.

|Typ položky|Typy zdrojových souborů|Formát výstupního souboru|
|---------------| - | - |
|**Kanál obsahu obrázku**|*Formát PNG*(Portable Network Graphics)<br /><br /> JPEG (*. jpg*, *. jpeg*, *. JPE*, *. jfif*)<br /><br /> Přímá nakreslená plocha (*. dds*)<br /><br /> Formát Graphics Interchange Format (*. gif*)<br /><br /> Rastrový obrázek (*. bmp*, *. DIB*)<br /><br /> Formát Tagged Image File Format (*. tif*, *. TIFF*)<br /><br /> Targa (*. tga*)|Plocha DirectDraw (*. dds*)|
|**Kanál obsahu sítě**|Soubor AutoDesk FBX Interchange (*. FBX*)<br /><br /> Soubor soubor Collada DAE (*. DAE*)<br /><br /> Soubor Wavefront OBJ (*. obj*)|soubor prostorové mřížky (*. marketingový ředitel*)|
|**Kanál obsahu shaderu**|Graf vizuálních shaderů (*. DGSL*)|Kompilovaný výstup shaderu (*. CSO*)|

## <a name="configure-asset-content-pipeline-properties"></a>Konfigurace vlastností kanálu obsahu prostředku

Vlastnosti kanálu obsahu jednotlivých souborů assetů můžete nastavit tak, aby se vytvořil konkrétnímu způsobu.

### <a name="to-configure-content-pipeline-properties"></a>Konfigurace vlastností kanálu obsahu

1. V **Průzkumník řešení**v projektu otevřete místní nabídku pro soubor assetu a zvolte možnost **vlastnosti**.

   Zobrazí se dialogové okno **Stránka vlastností** prostředku.

2. Ujistěte se, že vlastnosti **Konfigurace** a **platforma** jsou nastaveny na hodnoty, na které chcete změny použít.

3. V části **Vlastnosti konfigurace**vyberte uzel Content Pipeline (například **kanál obsahu obrázku** pro prostředky textury a image) a pak v mřížce vlastností nastavte vlastnosti na příslušné hodnoty. Pokud například chcete generovat mipmapy pro prostředek textury v čase sestavení, nastavte vlastnost **Generovat MIPS** na **Ano**.

4. Klikněte na tlačítko **OK** .

### <a name="image-content-pipeline-configuration"></a>Konfigurace kanálu obsahu obrázku

Použijete-li nástroj pro vytváření textur obsahu k sestavení prostředků textury, lze texturu zkomprimovat různými způsoby, označit, zda mají být v době sestavení generovány úrovně MIP, a změnit název výstupního souboru.

|Vlastnost|Popis|
|--------------|-----------------|
|**Komprimují**|Určuje typ komprese, který se používá pro výstupní soubor.<br /><br /> Dostupné jsou tyto možnosti:<br /><br /> -   **Bez komprese**<br />-   **BC1_UNORM komprese**<br />-   **BC1_UNORM_SRGB komprese**<br />-   **BC2_UNORM komprese**<br />-   **BC2_UNORM_SRGB komprese**<br />-   **BC3_UNORM komprese**<br />-   **BC3_UNORM_SRGB komprese**<br />-   **BC4_UNORM komprese**<br />-   **BC4_SNORM komprese**<br />-   **BC5_UNORM komprese**<br />-   **BC5_SNORM komprese**<br />-   **BC6H_UF16 komprese**<br />-   **BC6H_SF16 komprese**<br />-   **BC7_UNORM komprese**<br />-   **BC7_UNORM_SRGB komprese**<br /><br /> Informace o tom, které formáty komprese jsou podporovány v různých verzích rozhraní DirectX, najdete v tématu [Průvodce programováním pro DXGI](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews).|
|Převést na předem vynásobený formát alfa|**Ano** , pokud chcete převést obrázek na předem vynásobený formát alfa ve výstupním souboru; v opačném případě **ne**. Dojde ke změně pouze výstupního souboru, zdrojový obrázek zůstane beze změny.|
|**Generovat MIPS**|**Ano** , pokud chcete vygenerovat úplný řetěz mip v čase sestavení a zahrnout ho do výstupního souboru; v opačném případě **ne**. Pokud **ne**a zdrojový soubor již obsahuje mipmap řetězec, bude mít výstupní soubor řetězec MIP; v opačném případě výstupní soubor nebude mít žádný řetězec MIP.|
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité informace:**  Změna přípony názvu souboru výstupního souboru nemá žádný vliv na formát souboru.|

### <a name="mesh-content-pipeline-configuration"></a>Konfigurace kanálu obsahu sítě

Když použijete nástroj pro vytvoření mřížky obsahu sítě, můžete změnit název výstupního souboru.

|Vlastnost|Popis|
|--------------|-----------------|
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité informace:**  Změna přípony názvu souboru výstupního souboru nemá žádný vliv na formát souboru.|

### <a name="shader-content-pipeline-configuration"></a>Konfigurace kanálu obsahu shaderu

Při použití nástroje shader Content Pipeline k sestavení assetu shaderu můžete změnit název výstupního souboru.

|Vlastnost|Popis|
|--------------|-----------------|
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité informace:**  Změna přípony názvu souboru výstupního souboru nemá žádný vliv na formát souboru.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Načtení a použití 3D prostředků v době běhu

### <a name="use-textures-and-images"></a>Používání textur a imagí

Rozhraní Direct3D poskytuje funkce pro vytváření prostředků textury. V rozhraní Direct3D 11 poskytuje knihovna nástrojů D3DX11 další funkce pro vytváření prostředků textury a zobrazení prostředků přímo z obrazových souborů. Další informace o tom, jak vytvořit prostředek textury v Direct3D 11, najdete v tématu [textury](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures). Další informace o tom, jak pomocí knihovny D3DX11 vytvořit prostředek textury nebo zobrazení prostředků z obrázkového souboru, naleznete v tématu [How to: Initialize a Texture from a File](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to).

### <a name="use-3d-models"></a>Použití 3D modelů

Direct3D 11 neposkytuje funkce pro vytváření prostředků z 3D modelů. Místo toho musíte napsat kód, který přečte soubor 3D model a vytvoří vyrovnávací paměti vrcholů a indexů, které reprezentují 3D model a všechny prostředky, které model vyžaduje – například textury nebo shadery.

### <a name="use-shaders"></a>Použít shadery

Rozhraní Direct3D poskytuje funkce pro vytváření prostředků shaderu a jejich vazbu na programovatelné grafické kanály. Další informace o tom, jak vytvořit prostředek shaderu v rozhraní Direct3D a vytvořit jeho propojení s kanálem, najdete v tématu [Průvodce programováním pro HLSL](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide).

V programovatelném grafickém kanálu musí každá fáze kanálu poskytnout další fázi kanálu, která je naformátována způsobem, který dokáže pochopit. Vzhledem k tomu, že návrhář shaderů může vytvářet pouze pixel shadery, znamená to, že je až do vaší aplikace, aby se zajistilo, že data, která obdrží, jsou ve formátu, který očekává. Několik programovatelných fází shaderu nastává před shaderem pixel a provádění geometrických transformací – shader vrcholů, shader trupu, shader domény a shader geometrie. K neprogramovatelné fázi teselace dojde také před shaderem pixel. Bez ohledu na to, které z těchto fází přímo předchází pixel shader, musí mít výsledek v tomto formátu:

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

V závislosti na uzlech návrháře shaderu, které používáte ve shaderu, může být také nutné zadat další data ve formátu podle těchto definicí:

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Export textury obsahující mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Popisuje, jak pomocí kanálu obsahu obrázku exportovat texturu obsahující předpočítané mipmapy.|
|[Postupy: Export textury s přednásobeným alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Popisuje způsob použití kanálu obsahu obrázku k exportu textury, která obsahuje předem vynásobené hodnoty alfa.|
|[Postupy: Export textury pro použití s aplikacemi Direct2D nebo JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Popisuje, jak pomocí kanálu obsahu obrázku exportovat texturu, kterou lze použít v aplikaci Direct2D nebo JavaScript.|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Popisuje nástroje pro úpravy, které Visual Studio poskytuje k vytváření a manipulaci s 3D prostředky, které zahrnují textury a obrázky, 3D modely a shadery.|
|[Postupy: Export shaderu](../designers/how-to-export-a-shader.md)|Popisuje, jak exportovat shader z Návrháře shaderu.|
