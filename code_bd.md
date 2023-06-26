CREATE TABLE IF NOT EXISTS performer
(
	performer_id integer PRIMARY KEY,
  	name varchar(20) NOT NULL
);

CREATE TABLE if NOT EXISTS genre
(
	genre_id integer PRIMARY KEY,
  	name varchar(40) UNIQUE NOT NULL,
  	desckription varchar(128) NOT NULL
);

CREATE TABLE if NOT EXISTS album
(
	album_id integer PRIMARY KEY,
  	name varchar(40) NOT NULL,
  	year varchar(4)
);

CREATE TABLE IF NOT EXISTS track
(
	track_id integer PRIMARY KEY,
  	name varchar(40) Not NULL,
  	duration integer NOT NULL,
  	album_id integer REFERENCES album(album_id) NOT NULL
);

CREATE TABLE if not EXISTS assebler
(
	assembler_id integer PRIMARY KEY,
  	name varchar(40) NOT NULL,
  	year varchar(4)
);

CREATE TABLE if NOT exists performer_ganre
(
	performer_id integer REFERENCES performer(performer_id) NOT NULL,
  	genre_id integer REFERENCES genre(genre_id) NOT NULL,
  	
  	CONSTRAINT performer_ganre_pkey PRIMARY KEY (performer_id, genre_id)
);

CREATE table if not EXISTS genre_album
(
	genre_id integer REFERENCES genre(genre_id) NOT NULL,
  	album_id integer REFERENCES album(album_id) not NULL,
  
  	CONSTRAINT genre_album_pkey PRIMARY KEY (genre_id, album_id)
);

CREATE table if not EXISTS track_assembler
(
	track_id integer REFERENCES track(track_id) NOT NULL,
  	assembler_id REFERENCES assembler(assembler_id) NOT NULL,
  
  	CONSTRAINT track_assembler_pkey PRIMARY key (track_id, assembler_id)
)