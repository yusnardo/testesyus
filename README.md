# testesyus



DROP table  IF EXISTS COURSES ;     
CREATE TABLE COURSES
(
  id_courses  serial  NOT NULL,
  name_course VARCHAR DEFAULT 100,
  desc_course VARCHAR DEFAULT 100,
  create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
  update_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
  PRIMARY KEY (id_courses)
);


DROP table IF EXISTS STUDENT;    
CREATE TABLE STUDENT
(
  id_student serial NOT NULL,
  name       VARCHAR DEFAULT 50,
  age        VARCHAR DEFAULT 2,
  address        VARCHAR DEFAULT 250,
  phone_number   VARCHAR DEFAULT 20,
  create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
  update_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
  PRIMARY KEY (id_student)
);

DROP table  IF EXISTS UNIVERSITY; 
CREATE TABLE UNIVERSITY
(
  id_university serial NOT NULL,
  name          VARCHAR DEFAULT 100,
  description   VARCHAR DEFAULT 200,
  id_city       INT     NOT NULL DEFAULT 11,
  create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
  update_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
  PRIMARY KEY (id_university)

);



DROP table  IF exists COURSE_STUDENT;     
CREATE TABLE COURSE_STUDENT
(
  id_student INT NOT NULL DEFAULT 11,
  id_courses INT NOT NULL DEFAULT 11,
  FOREIGN KEY (id_student) REFERENCES STUDENT (id_student),
  FOREIGN KEY (id_courses) REFERENCES COURSES (id_courses)
);

DROP table  IF EXISTS UNIVERSITY_COURSE;
CREATE TABLE UNIVERSITY_COURSE
(
  id_university INT NOT NULL DEFAULT 11,
  id_courses    INT NOT NULL DEFAULT 11,
  FOREIGN KEY (id_university) REFERENCES UNIVERSITY (id_university),
  FOREIGN KEY (id_courses) REFERENCES COURSES (id_courses)
);

DROP table IF EXISTS UNIVERSITY_STUDENT;
CREATE TABLE UNIVERSITY_STUDENT
(
  id_student    INT NOT NULL DEFAULT 11,
  id_university INT NOT NULL DEFAULT 11,
  FOREIGN KEY (id_student) REFERENCES STUDENT (id_student),
  FOREIGN KEY (id_university) REFERENCES UNIVERSITY (id_university)
);

CREATE TABLE city
(
  id_city INT     NOT NULL DEFAULT 11,
  city    VARCHAR DEFAULT 50,
  PRIMARY KEY (id_city)
);

CREATE TABLE map_course_student
(
  id_student INT NOT NULL DEFAULT 11,
  id_courses INT NOT NULL DEFAULT 11
);

CREATE TABLE map_course_university
(
  id_university INT NOT NULL DEFAULT 11,
  id_courses    INT NOT NULL DEFAULT 11
);

CREATE TABLE map_university_student
(
  id_student    INT NOT NULL DEFAULT 11,
  id_university INT NOT NULL DEFAULT 11
);

ALTER TABLE map_course_student
  ADD CONSTRAINT FK_student_TO_map_course_student
    FOREIGN KEY (id_student)
    REFERENCES student (id_student);
 
   
   
ALTER TABLE map_course_student
  ADD CONSTRAINT FK_courses_TO_map_course_student
    FOREIGN KEY (id_courses)
    REFERENCES courses (id_courses);

ALTER TABLE university
  ADD CONSTRAINT FK_city_TO_university
    FOREIGN KEY (id_city)
    REFERENCES city (id_city);

ALTER TABLE map_course_university
  ADD CONSTRAINT FK_university_TO_map_course_university
    FOREIGN KEY (id_university)
    REFERENCES university (id_university);

ALTER TABLE map_course_university
  ADD CONSTRAINT FK_courses_TO_map_course_university
    FOREIGN KEY (id_courses)
    REFERENCES courses (id_courses);

ALTER TABLE map_university_student
  ADD CONSTRAINT FK_student_TO_map_university_student
    FOREIGN KEY (id_student)
    REFERENCES student (id_student);

ALTER TABLE map_university_student
  ADD CONSTRAINT FK_university_TO_map_university_student
    FOREIGN KEY (id_university)
    REFERENCES university (id_university);
