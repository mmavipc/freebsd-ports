# Created by: Roman Bogorodskiy
# $FreeBSD$

PORTNAME=	MP3-Tag
PORTVERSION=	1.13
CATEGORIES=	audio perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	novel@FreeBSD.org
COMMENT=	Module for reading tags of MP3 audio files

USES=		perl5
NO_STAGE=	yes
USE_PERL5=	configure

MAN1=		audio_rename.1 typeset_audio_dir.1 mp3info2.1
MAN3=		MP3::Tag.3 MP3::Tag::ID3v1.3 MP3::Tag::File.3 \
		MP3::Tag::CDDB_File.3 MP3::Tag::ParseData.3 MP3::Tag::Inf.3 \
		MP3::Tag::ID3v2.3 MP3::Tag::ID3v2_Data.3 MP3::Tag::LastResort.3 \
		MP3::Tag::Cue.3 Normalize::Text::Music_Fields.3 MP3::Tag::ImageSize.3 \
		MP3::Tag::ImageExifTool.3

CONFLICTS=	p5-tagged-0.*

.include <bsd.port.mk>
